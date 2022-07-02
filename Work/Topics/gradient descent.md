# Gradient Descent

---
When we're dealing with [[machine learning]] [[modeling|models]], we need to optimize all the parameters inside of it to reach the best result we can. Gradient descent is a computationally-light way of doing that. 

The first step is to apply a [[loss function]] to the model output. We use some kind of [[metrics|metric]] to quantify the error in the model, such as [[MAE]] or the [[coefficient of determination]]. We can also include a [[regularization]] term in this loss function. 

Now that we have a loss function, the task is to minimize this function by changing model parameters. 

We now turn to the power of the [[derivatives|derivative]]. By finding the derivative of the loss function at a given point, we can see what the instantaneous slope is at that point. 

The way that gradient descent works in two dimensions is that we start at some point $x_n$. We have to decide which point to check next, and we call the method by which this next point to check is calculated the ==update rule==. The simplest update rule is...

$$x_{n+1} = x_n - \frac{df}{dx}(x_n)$$

... where $x_{n+1}$ is the next point we want to check. We just take the current value of *x* and subtract whatever we find the derivative of that point to be. 

Let's look at an example. 

Let's say that we want to find the local minimum of the function $f(x)=x^2$. Now we know that this is at the point $x=0$, but let's pretend we don't. 

If we start at $x_n=10$, we could use this equation...

$$x_{n+1} = x_n - \frac{df}{dx}(x_n)$$
$$x_{n+1} = 10 - \frac{df}{dx}10^2$$
$$x_{n+1} = 10 - 20 = -10$$

Wait, what happened here? Now we're checking the point $x=-10$, and we've skipped over the local minimum entirely! 

Now we see the need for another variable in this equation, $\alpha$, the ==learning rate==. This variable will be somewhere between 0 and 1, so that it helps set the maximum step distance every time we move to check a new number. 

For the above example, a step rate of 0.5 would mean that we check the point $x=10$, then we arrive at the point zero on the next step. We have two considerations when choosing a learning rate. If we choose a rate too large, we risk skipping over the minimum point. If the learning rate is too small, we sacrifice time spent making steps down the curve. 

In order to apply this concept to models that have more than one feature (aka more than two dimensions), we have to generalize the above formula. 

$$ \nabla f = (
\frac{\partial f}{\partial x_1}+
\frac{\partial f}{\partial x_2}+...
+\frac{\partial f}{\partial x_n}
)
$$
... where $\partial$ indicates that we are taking the partial derivative of the function, one variable at a time. We then sum these partial [[derivatives]]. We then apply each partial derivative to that part of the function. 

For example, we can do this in two dimensions. If we work with the function $f(x,y)=x^2+2y^2$...

$$
\nabla f(x,y) = (
\frac{\partial f}{\partial x}+\frac{\partial f}{\partial y}
)
$$

If we started at the point (20,40), we could find the next point to check this way...

$$(x_n, y_n) = \nabla f(x,y)$$
$$(x_n, y_n) = \frac{\partial f}{\partial x}+$$

---
1. [[1-20-21 metis#Lecture gradient descent]]