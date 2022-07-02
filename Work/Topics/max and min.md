# Maximum and Minimum
`LINKS:`
`TAGS:`

---
## Introduction
A big use for [[derivatives]] is to find the local maximums and minimums of [[functions (python)]]. This will come into play when we try and optimize algorithms. 

Wherever the derivative of a function equals zero, the local slope must be zero, meaning that this is either a minimum or maximum point. For instance, in the $x^2$ parabola, the only place the slope is zero is at the origin, which is the minimum of the function. By setting the derivative to zero, we can find these points. 

Don’t get caught thinking there is only one local min / max when there might be more! For the function $x^3-1$, the derivative is $3x^2$. If we set this to zero, we get x = 1/3, but be careful. This function has changes in direction at both the positive and negative 1/3 points. 

## Concavity / convexity
When we take a second derivative, we can learn even more. A positive 2nd deriv will be convex (U shaped). A negative 2nd deriv will be concave (n shaped).

Therefore, we can see if a local change of direction is a max or a min based on the second derivative. 

$$f(x) = 60x-x^2$$

$$f'(x) = 60-2x$$

$$ f''(x) = -2 $$

Since the second derivative is negative, we know that we can find a local maximum where f'(x) = 0. 