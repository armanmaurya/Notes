It is a expansion of a [Periodic function](Periodic%20function.md) into a sum of trigonometric functions. The Fourier series is an example of a trigonometric series.
$$f(x) = a_{o} + \sum_{n=1}^\infty (a_{n} \cos nx + b_{n} \sin nx); \quad \alpha < x < a+2\pi$$
Where, 
$$a_{o} = \frac{1}{2\pi} \int_{\alpha}^{\alpha + 2\pi} f(x) \, dx $$

$$a_{n} = \frac{1}{\pi}\int _{\alpha}^{\alpha+2\pi} f(x) \cos nx \, dx $$

$$b_{n} = \frac{1}{\pi} \int _{\alpha}^{\alpha + 2\pi} f(x) \sin nx \, dx $$
By expressing a function as a sum of sines and cosines, many problems involving the function become easier to analyze because trigonometric functions are well understood.

The coefficients of the Fourier series are determined by integrals of the function multiplied by trigonometric functions, 

>[!info]- Example-1 
>What you want 
>Noting 