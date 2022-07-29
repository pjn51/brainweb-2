---
rating: 
author: Numberphile
genre: non-fiction
---
# The Mandelbrot Set - Numberphile (2014)
`SOURCE:` [source](https://www.youtube.com/watch?v=NGMRB4O922I)
 #video 

---
We can generate the [[Mandelbrot set]] on the *complex plane.* The complex plane is the plane of *complex numbers* ([[Complex numbers are combinations of real and imaginary numbers]]). 

Complex numbers take the form of $a+bi$, where $a$ is the real part, and $bi$ is the imaginary part. $i$ represents an [[imaginary numbers|imaginary number]] scaled by real number $b$. 

On the x-axis of the complex plane we have the real axis of $a$, while we have the imaginary axis along the y-axis, measuring the size of $bi$. 

We can measure the *magnitude* of complex number $z$ which is the distance from the center of the plane to the point $z$. We can write this as $|z|$ or as $|a+bi|$.  

In order to calculate the Mandelbrot set, we plug $z$ into a function $f_c(z) = z^2+c$, where $c$ is also a complex number. 

If we take complex num $c$ and associate it with the following function that takes input complex num $z$ and outputs $z^2+c$. 

We're interested in what happens to the magnitude of $z$ as we *iterate* it through this function (we take the output of the function and put it back through the function as an input). 

Lets see what happens when we do this with the exact center of the complex plane, the point where $a$ and $b$ are both zero. Lets make $c=1$ for now and see what happens.  


$$
f_1(0) = 0^2+1 = 1
$$
$$
f_1(1) = 1^2 + 1 = 2
$$
$$
f_1(2)=2^2+1=5
$$

If we continue this process, we can see the behavior of zero under iteration for the value of $c=1$. 

The mandelbrot set is concerned with what happens to the size of these numbers, meaning the magnitude of the complex number we were talking about earlier. 

Whenever we plug a compex number in for $c$, we always see one of two outcomes. The first outcome is that sooner or later, the magnitude of $z$ gets really really large. We call this "case one." 

On the other hand, sometimes we see that the magnitude of $z$ might never get that large. We call that "case two." 

One or the other must happen when $c$ is a complex number and we iterate $z$ as zero through the above function. Either the distance of the iterates to zero will go to infinity, or it won't. 

Let's illustrate something from case two, if we define $z$ as zero and $c$ as $-1$:
$$
f_{-1}(z) = z^2-1
$$$$
f_{-1}(0) = -1
$$$$
f_{-1}(-1) = 0
$$$$
f_{-1}(0) = -1
$$ Et certa, forever. The iterates just alternate and never go anywhere. This is an example of case 2. 

The definition on the Mandelbrot set, $M$, is the set of $c$ complex number for which case 2 holds (it never iterates towards infinity). We can shade the graph based on how many iterations it takes to get really big, and that's how the cool images that we see are developed. 

The axes that we use when drawing the set are usually limited to a maximum of 2, since any value for $c$ over two will iterate to infinity all the time. 

The edges of this set are really interesting. In the boundary regions, changing $c$ by a tiny amount can drastically change the magnitude of the iterations. When we zoom into the edge of the set, we can see that [[The Mandelbrot set provides seemingly infinite complexity]] in the details of the edge. 