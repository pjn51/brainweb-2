# Integrals


---
# Introduction
An integral is basically an anti-[[derivatives|derivative]]. We use it to find the area under a curve, which is useful when calculating the [[probability]] of a continuous variable being equal or less, or equal or more, than a specific value. This is useful for tests regarding [[statistics]], and is a fundamental component of [[calculus]].

This is the form we write integrals in...

$$ \int_{a}^{b} f(x) \,dx$$

We are finding the area under the curve defined by f(x) from point *a* to point *b*.

First, we have to basically reverse the normal derivative rules. Here's an example...

$$\int_{0}^{3} x^2 \,dx$$
For $f(x) = x^2$, we increase the exponent by one, and then we divide by that increased exponent. We add C to account for any constants that would be erased by deriviation...
$$\int_{0}^{3} \frac{x^{2+1}}{(2+1)}+C $$
Now that we have taken the anti-derivative, we can find the area under the curve

# Finding the area under the curve
After we have taken the integral, all that is left to do is to plug in *b* and subtract it from *a*. For the example above...
$$\int_{0}^{3} \frac{x^3}{3} = (\frac{3^3}{3}+C)-(\frac{0^3}{3}+C) = 9 - 0 = 9 $$
Therefore we can say with confidence that there is a value of 9 beneath the curve of x^2 between zero and three! Note that *C* cancels out. 

# Applications
...