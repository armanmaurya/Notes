### Integrand is a Function of Another Function 
If the integral is of the form,
$$
\int f[\phi(x)]\phi(x) \, dx
$$ 
Then we put $\phi(x) = t$ so that $\phi(x)dx = dt$. Now integral is reduced,
$$
\int f(t) \, dt
$$

---
**Note:-**
In this method the function is broken into two factors so that one factor can be expressed in terms of the function whose differential coefficient is the second factor.

In case of objective question in which direct indefinite integration is asked, function being very complicated to integrate, then try differentiating the options.

---
### Integrand is the Product of Function and its Derivative
If the integral is of the form $I = \int f(x)f(x) \, dx$, we put $f(x) = t$ and convert it into a standard integral.

### Integrand is a Function of the Form f (ax+b)
Here we put ax+b = t and convert it into a standard integral. Now if, 
$$
\int f(x) \, dx = \phi (x) 
$$
Then, 
$$
\int f(ax+b) \, dx = \frac{1}{a}\phi(ax+b) 
$$
### Integral of the Form
$$
\int\cfrac{dx}{a\sin x + b\cos x}
$$
then Substitute $a = r\cos \theta$ and $b = r\sin \theta$, $\tan \theta = \frac{b}{/a} \implies \theta = \tan^{-1}\left( \frac{b}{a} \right)$, we get
$$I = \int \cfrac{dx}{r\sin (x+\theta)} = \frac{1}{r} \int \text{cosec}(x+ \theta)dx = \frac{1}{r}\log \tan\left( \frac{x + \theta}{2}\right) \, dx$$

---
Related Links:-
- [Method Of Integration](Method%20Of%20Integration.md) 
