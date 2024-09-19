_How do I fully replace the username field with an email field for Django authentication?_

This article explains step-by-step how to create a custom [user model](https://docs.djangoproject.com/en/4.1/ref/contrib/auth/#user-model) in Django so that an email address can be used as the primary user identifier instead of a username for authentication.

> Keep in mind that the process outlined in this article requires significant changes to the database schema. Because of this, it's only recommended for new projects. If you're working on an existing legacy project, you'll need to follow a different set of steps. For more on this, review the [Migrating to a Custom User Model Mid-project in Django](https://testdriven.io/blog/django-custom-user-model-migration/) article.

## Objectives

By the end of this article, you should be able to:

1.  Describe the difference between `AbstractUser` and `AbstractBaseUser`
2.  Explain why you should set up a custom user model when starting a new Django project
3.  Start a new Django project with a custom user model
4.  Use an email address as the primary user identifier instead of a username for authentication
5.  Practice test-first development while implementing a custom user model

## AbstractUser vs AbstractBaseUser

The default user model in Django uses a username to uniquely identify a user during authentication. If you'd rather use an email address, you'll need to create a custom user model by either subclassing `AbstractUser` or `AbstractBaseUser`.

Options:

1.  `AbstractUser`: Use this option if you are happy with the existing fields on the user model and just want to remove the username field.
2.  `AbstractBaseUser`: Use this option if you want to start from scratch by creating your own, completely new user model.

> We'll look at both options, `AbstractUser` and `AbstractBaseUser`, in this article.

The steps are the same for each:

1.  Create a custom user model and Manager
2.  Update _settings. Py_
3.  Customize the `UserCreationForm` and `UserChangeForm` forms
4.  Update the admin

> It's [highly recommended](https://docs.djangoproject.com/en/4.1/topics/auth/customizing/#using-a-custom-user-model-when-starting-a-project) to set up a custom user model when starting a new Django project. Without it, you will need to create another model (like `UserProfile`) and link it to the Django user model with a `OneToOneField` if you want to add new fields to the user model.

## Project Setup

Start by creating a new Django project along with a users app:

```text
$ mkdir django-custom-user-model && cd django-custom-user-model
$ python3 -m venv env
$ source env/bin/activate

(env)$ pip install Django==4.1.5
(env)$ django-admin startproject hello_django .
(env)$ python manage.py startapp users
```

> Feel free to swap out virtualenv and Pip for [Poetry](https://python-poetry.org/) or [Pipenv](https://github.com/pypa/pipenv). For more, review [Modern Python Environments](https://testdriven.io/blog/python-environments/).

DO NOT apply the migrations. Remember: You must create the custom user model _before_ you apply your first migration.

Add the new app to the `INSTALLED_APPS` list in _settings. Py_:

```text
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",

    "users",  # new
]
```


## Model Manager

First, we need to add a custom [Manager](https://docs.djangoproject.com/en/4.1/topics/db/managers/), by subclassing `BaseUserManager`, that uses an email as the unique identifier instead of a username.

Create a _managers. Py_ file in the "users" directory:

```text
from django.contrib.auth.base_user import BaseUserManager
from django.utils.translation import gettext_lazy as _


class CustomUserManager(BaseUserManager):
    """
    Custom user model manager where email is the unique identifiers
    for authentication instead of usernames.
    """
    def create_user(self, email, password, **extra_fields):
        """
        Create and save a user with the given email and password.
        """
        if not email:
            raise ValueError(_("The Email must be set"))
        email = self.normalize_email(email)
        user = self.model(email=email, **extra_fields)
        user.set_password(password)
        user.save()
        return user

    def create_superuser(self, email, password, **extra_fields):
        """
        Create and save a SuperUser with the given email and password.
        """
        extra_fields.setdefault("is_staff", True)
        extra_fields.setdefault("is_superuser", True)
        extra_fields.setdefault("is_active", True)

        if extra_fields.get("is_staff") is not True:
            raise ValueError(_("Superuser must have is_staff=True."))
        if extra_fields.get("is_superuser") is not True:
            raise ValueError(_("Superuser must have is_superuser=True."))
        return self.create_user(email, password, **extra_fields)
```

Decide which option you'd like to use: subclassing `AbstractUser` or `AbstractBaseUser`.

### AbstractUser

Update _users/models. Py_:

```text
from django.contrib.auth.models import AbstractUser
from django.db import models
from django.utils.translation import gettext_lazy as _

from .managers import CustomUserManager


class CustomUser(AbstractUser):
    username = None
    email = models.EmailField(_("email address"), unique=True)

    USERNAME_FIELD = "email"
    REQUIRED_FIELDS = []

    objects = CustomUserManager()

    def __str__(self):
        return self.email
```

Here, we:

1.  Created a new class called `CustomUser` that subclasses `AbstractUser`
2.  Removed the `username` field
3.  Made the `email` field required and unique
4.  Set the `USERNAME_FIELD` -- which defines the unique identifier for the `User` model -- to `email`
5.  Specified that all objects for the class come from the `CustomUserManager`

### AbstractBaseUser

Update _users/models. Py_:

```text
from django.contrib.auth.models import AbstractBaseUser, PermissionsMixin
from django.db import models
from django.utils import timezone
from django.utils.translation import gettext_lazy as _

from .managers import CustomUserManager


class CustomUser(AbstractBaseUser, PermissionsMixin):
    email = models.EmailField(_("email address"), unique=True)
    is_staff = models.BooleanField(default=False)
    is_active = models.BooleanField(default=True)
    date_joined = models.DateTimeField(default=timezone.now)

    USERNAME_FIELD = "email"
    REQUIRED_FIELDS = []

    objects = CustomUserManager()

    def __str__(self):
        return self.email
```

Here, we:

1.  Created a new class called `CustomUser` that subclasses `AbstractBaseUser`
2.  Added fields for `email`, `is_staff`, `is_active`, and `date_joined`
3.  Set the `USERNAME_FIELD` -- which defines the unique identifier for the `User` model -- to `email`
4.  Specified that all objects for the class come from the `CustomUserManager`

## Settings

Add the following line to the _settings. Py_ file so that Django knows to use the new custom user class:

```text
AUTH_USER_MODEL = "users.CustomUser"
```

Now, you can create and apply the migrations, which will create a new database that uses the custom user model. Before we do that, let's look at what the migration will actually look like _without_ creating the migration file, with the [\--dry-run](https://docs.djangoproject.com/en/4.1/ref/django-admin/#cmdoption-makemigrations-dry-run) flag:

```text
(env)$ python manage.py makemigrations --dry-run --verbosity 3
```

You should see something similar to:

```text
# Generated by Django 4.1.5 on 2023-01-21 20:36

from django.db import migrations, models
import django.utils.timezone


class Migration(migrations.Migration):

    initial = True

    dependencies = [
        ('auth', '0012_alter_user_first_name_max_length'),
    ]

    operations = [
        migrations.CreateModel(
            name='CustomUser',
            fields=[
                ('id', models.BigAutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('password', models.CharField(max_length=128, verbose_name='password')),
                ('last_login', models.DateTimeField(blank=True, null=True, verbose_name='last login')),
                ('is_superuser', models.BooleanField(default=False, help_text='Designates that this user has all permissions without explicitly assigning them.', verbose_name='superuser status')),
                ('first_name', models.CharField(blank=True, max_length=150, verbose_name='first name')),
                ('last_name', models.CharField(blank=True, max_length=150, verbose_name='last name')),
                ('is_staff', models.BooleanField(default=False, help_text='Designates whether the user can log into this admin site.', verbose_name='staff status')),
                ('is_active', models.BooleanField(default=True, help_text='Designates whether this user should be treated as active. Unselect this instead of deleting accounts.', verbose_name='active')),
                ('date_joined', models.DateTimeField(default=django.utils.timezone.now, verbose_name='date joined')),
                ('email', models.EmailField(max_length=254, unique=True, verbose_name='email address')),
                ('groups', models.ManyToManyField(blank=True, help_text='The groups this user belongs to. A user will get all permissions granted to each of their groups.', related_name='user_set', related_query_name='user', to='auth.group', verbose_name='groups')),
                ('user_permissions', models.ManyToManyField(blank=True, help_text='Specific permissions for this user.', related_name='user_set', related_query_name='user', to='auth.permission', verbose_name='user permissions')),
            ],
            options={
                'verbose_name': 'user',
                'verbose_name_plural': 'users',
                'abstract': False,
            },
        ),
    ]
```

> If you went the `AbstractBaseUser` route, you won't have fields for `first_name` or `last_name`. Why?

Make sure the migration does not include a `username` field. Then, create and apply the migration:

```text
(env)$ python manage.py makemigrations
(env)$ python manage.py migrate
```

View the schema:

```text
$ sqlite3 db.sqlite3

SQLite version 3.28.0 2019-04-15 14:49:49
Enter ".help" for usage hints.

sqlite> .tables

auth_group                         django_migrations
auth_group_permissions             django_session
auth_permission                    users_customuser
django_admin_log                   users_customuser_groups
django_content_type                users_customuser_user_permissions

sqlite> .schema users_customuser

CREATE TABLE IF NOT EXISTS "users_customuser" (
  "id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "password" varchar(128) NOT NULL,
  "last_login" datetime NULL,
  "is_superuser" bool NOT NULL,
  "first_name" varchar(150) NOT NULL,
  "last_name" varchar(150) NOT NULL,
  "is_staff" bool NOT NULL,
  "is_active" bool NOT NULL,
  "date_joined" datetime NOT NULL,
  "email" varchar(254) NOT NULL UNIQUE
);
```

> If you went the `AbstractBaseUser` route, why is `last_login` part of the model?

You can now reference the user model with either `get_user_model()` or `settings.AUTH_USER_MODEL`. Refer to [Referencing the User model](https://docs.djangoproject.com/en/4.1/topics/auth/customizing/#referencing-the-user-model) from the official docs for more info.

Also, when you create a superuser, you should be prompted to enter an email rather than a username:

```text
(env)$ python manage.py createsuperuser

Email address: test@test.com
Password:
Password (again):
Superuser created successfully.
```

Make sure the tests pass:

```text
(env)$ python manage.py test

Creating test database for alias 'default'...
System check identified no issues (0 silenced).
..
----------------------------------------------------------------------
Ran 2 tests in 0.282s

OK
Destroying test database for alias 'default'...
```

## Forms

Next, let's subclass the `UserCreationForm` and `UserChangeForm` forms so that they use the new `CustomUser` model.

Create a new file in "users" called _forms. Py_:

```text
from django.contrib.auth.forms import UserCreationForm, UserChangeForm

from .models import CustomUser


class CustomUserCreationForm(UserCreationForm):

    class Meta:
        model = CustomUser
        fields = ("email",)


class CustomUserChangeForm(UserChangeForm):

    class Meta:
        model = CustomUser
        fields = ("email",)
```

## Admin

Tell the admin to use these forms by subclassing `UserAdmin` in _users/admin. Py_:

```text
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin

from .forms import CustomUserCreationForm, CustomUserChangeForm
from .models import CustomUser


class CustomUserAdmin(UserAdmin):
    add_form = CustomUserCreationForm
    form = CustomUserChangeForm
    model = CustomUser
    list_display = ("email", "is_staff", "is_active",)
    list_filter = ("email", "is_staff", "is_active",)
    fieldsets = (
        (None, {"fields": ("email", "password")}),
        ("Permissions", {"fields": ("is_staff", "is_active", "groups", "user_permissions")}),
    )
    add_fieldsets = (
        (None, {
            "classes": ("wide",),
            "fields": (
                "email", "password1", "password2", "is_staff",
                "is_active", "groups", "user_permissions"
            )}
        ),
    )
    search_fields = ("email",)
    ordering = ("email",)


admin.site.register(CustomUser, CustomUserAdmin)
```

That's it. Run the server and log in to the admin site. You should be able to add and change users like normal.

![django admin](https://testdriven.io/static/images/blog/django/django-custom-user-model/admin-site.png)

## Conclusion

In this article, we looked at how to create a custom user model so that an email address can be used as the primary user identifier instead of a username for authentication.

You can find the final code for both options, `AbstractUser` and `AbstractBaseUser`, in the [django-custom-user-model](https://github.com/testdrivenio/django-custom-user-model) repo. The final code examples include the templates, views, and URLs required for user authentication as well.

Want to learn more about customizing the Django user model? Check out the following resources:

1.  [Options & Objects: Customizing the Django User Model](https://medium.com/agatha-codes/options-objects-customizing-the-django-user-model-6d42b3e971a4)
2.  [How to Extend Django User Model](https://simpleisbetterthancomplex.com/tutorial/2016/07/22/how-to-extend-django-user-model.html)
3.  [Getting the Most Out of Django's User Model](https://www.youtube.com/watch?v=sXZ3ntGp_Xc) (video)
4.  [Customizing authentication in Django](https://docs.djangoproject.com/en/4.1/topics/auth/customizing/)