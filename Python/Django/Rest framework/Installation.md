In this article we are install  `djangorestframework` in out django project but before moving further please refer to [this](../Setup%20Project.md) article for project setup

After setting up project we can move further and install `djangorestframework` in out project,

Install using `pip` including any optional package you want...
```shell
pip install djangorestframework
pip install markdown      # Markdown support for the browsable API (optional)
pip install django-filter  # Filtering support (optional)
``` 

Add `'rest_framework'` to your `INSTALLED_APPS` setting.

```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```
If you're intending to use the browsable API you'll probably also want to add REST framework's login and logout views. Add the following to your root `urls.py` file.

```python
urlpatterns = [
    ...
    path('api-auth/', include('rest_framework.urls'))
]
```
Note that the url path can be whatever you want.