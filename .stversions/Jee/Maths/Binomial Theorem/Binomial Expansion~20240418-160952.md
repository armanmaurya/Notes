A binomial is an algebraic expression with two terms. For example, a+b, x-y, etc are binomials. We have as set of algebraic identities to find the expansion when binomial is raised to exponents 2 and 3. For example, $(a+b)^2=a^2+2ab+b^2$. But what if the exponents are bigger numbers? It is tedious to find the expansion manually. 

The **binomial expansion** formula eases this process and used to find the powers of the binomials which cannon be expanded using the algebraic identities. The binomial expansion formula involves binomial coefficients or combinatorial coefficient which are of form $\binom{n}{k}$ **or** $^nC_{r}$ and it is calculated using the formula,
$$
^nC_{r} = \frac{n!}{(n-r)! \ r!} = \frac{n(n-1)\dots \text{upto $r$ factor}}{r!}
$$
The binomial expansion formula is also know as the binomial theorem, formula is given by,
$$
(x+y)^n= \ ^nC_{0} x^ny^0+ \ ^nC_{1}x^{n-1}y^1+ \ ^nC_{2}x^{n-2}y^2 +\dots\dots+ \ ^nC_{n}x^0y^n
$$

### Important Points :
- The number of terms in the expansion of $(x+y)^n$ is $n+1$.
- The sum of powers of $x$ & $y$ in each term is $n$ 
-  Power of first variable $(x)$ **decreases** while of second variable $(y)$ **increases**.
- Compact Form of $(x+y)^n$ is $$\sum_{r=0}^n\ ^nC_{r}x^{n-r}y^r$$
- General Term $T_{r+1}$ is $$^nC_{r}x^{n-r}y^r$$ 

# Important Expansions:-
$$(1+x)^n = \sum_{r=0}^n \ ^nC_{r} x^r$$
$$(1-x)^n = \sum_{r=0}^n \ ^nC_{r}(-1)^r x^r$$
$$(x-y)^n = \sum_{r=0}^n \ ^nC_{r}x^{n-r}(-1)^r.y^r$$
