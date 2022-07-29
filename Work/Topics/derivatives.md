# Derivatives
`LINKS:` [[calculus]]


---
# Introduction
[[Derivatives measure rates of change]]. 

In [[calculus]], the derivative measures how the slope of a [[functions (python)|function]] changes across space. This means we have to take the slope of a line $f(x)$ and we end up with $f'(x)$ as the derivative. 

For instance, when looking at the exponential function $x^2$, we see that the slope increases as we move farther from the origin. This means that there must be a positive derivative for this function. As it turns out, the derivative of $x^2$ is just $2x$. 

Formally, a derivative is the slope of a [[trigonometry|tangent]] line that is touching the function line at a given point.

# Calculating analytically
We can try and use the formula for slope, $\frac{Δy}{Δx}$, to get the instantaneous slope of a single point. But the only way to do this algebraically is find the slope between two points that are vanishingly close together. However, we can’t really get all the way there using algebra. We have to use calculus!

We are going to have to use a limit. A limit such as lim a -> 0 tells us that in the following equation, we are making a as close to zero as possible. However, this is still used in the analytical solution, not the calculus solution. 

## A better way to calculate: derivative rules
Remember, the derivative tells you the instantaneous slope of a point on a line. 
Continuous functions are functions for which sufficiently small changes in x result in small changes in y. This means that whenever you change x a tiny bit, y also needs to change a tiny bit. Functions that have big gaps or something in the middle of them are not continuous, and we can't perform derivatives on them. 

## Common Derivatives
There are some shortcuts we can take to find derivatives, some common rules that we can remember that will almost always apply. 

$$f(x) = a*x^n +x+b $$

$$f’(x) = a*n*x^{n-1}+1$$

We bring down the exponent to the front, then lower x’s exponent by one whenever x is exponentiated. We remove all constants. 

This also means that wherever we find a non-exponentiated x, we remove it since the exponent lowers from one to zero.

This means that whenever an equation has a simple x in it, we bring down the exponent, one, and reduce the exponent above x by one, which makes it x0, which is one! So we get rid of it basically. 

| Original function    | derivative                    |
| -------------------- | ----------------------------- |
| $$f(x) = sin(x)$$    | $$f’(x) = cos(x)$$            |
| $$f(x) = cos(x)$$    | $$f’(x) = -sin(x)$$           |
| $$f(x) = ln(x)$$     | $$f’(x) = \frac{1}{x}$$       |
| $$f(x) = e^x$$       | $$f’(x) = e^x$$               |
| $$f(x) = \log_b(x)$$ | $$f’(x) = \frac{1}{ln(b)}*x$$ |
| $$f(x) = a^x$$       | $$f'(x) = \ln(a) * a*x$$      | 

## Additional Rules for Derivatives
#### Combining derivatives together
We can add derivatives together.
$$(f(x) + g(x))’ = f’(x) + g’(x)$$

It gets trickier to multiply them.  
$$(f(x) * g(x))’ = f’(x) * g(x) + g’(x) * f(x)$$
Composition: 

$$(f(g(x)))’ =  f’(g(x)) * g’(x)$$

$$\frac{d}{dx} (sin(x) + x2) = \frac{d}{dx} (sin(x)) + \frac{d}{dx} x2 = cos(x) + 2x$$

## Partial Derivatives
The idea here is to take the derivative one variable at a time in an equation with multiple variables. We treat the second variable as a constant while we find the partial derivative in regards to the first variable. 

$$f(x) = x2 - xy$$

$$\frac{d}{dx} = 2x-y$$

$$\frac{d}{dy} = -x$$

## Gradients
This is a [[scalars and vectors|vector]] with a length of the number of variables in the function that you’re taking the derivative of. This is denoted with an inverted triangle. 

For $$f(x_1,x_2) = x_1 * ln(x_2) + sin(x_1)$$

the gradient is...
							
							$$\begin{vmatrix}ln(x_2)+cos(x_1)\\x_1/x_2 \end{vmatrix}$$

# Example Problems
### 1
Calculate the derivative of $f(x) =3x^2+4$
$$
f(x)=3x^2+4
$$
$$
f'(x)=3*2x=6x
$$
### 2
Calculate the derivative of $f(x)=4^{ln(x)}+6x^3$

$$
f(x)=4^{ln(x)}+6x^3
$$
$$
f'(x)=\ln(4)*4*\frac{1}{x}+18x
$$
$$
f'(x)=\ln(4)*\frac{4}{x}+18x
$$