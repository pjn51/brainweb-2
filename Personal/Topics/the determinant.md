# The Determinant
`LINKS:` [[linear algebra]]

---
## Theory
In [[linear algebra]], we might notice how some [[linear transformation]]s seem to stretch space, while others compress it. We can measure how *much* a transformation stretches or squishes things.

Formally, we are measuring the factor by which the area of a given region increases or decreases due to a transformation. For example, a lin. transformation that doubles the magnitude of ihat and jhat would increase the amount of space taken up by the unit square of ihat and jhat. 

We keep track of this by keeping track of **the unit square** with side length ihat and jhat. Whatever happens to one square in the grid will happen to any other square, no matter the size. This is why we can simplify this aspect of the transformation. 

This means that if we know what factor the area of the grid square has changed by, we can multiply this same factor by the area of any original shape to find its new size. This factor is called **the determinant**. If a transformation increased the size of the unit square by a factor of three, the determinant would be 3. 

The determinant would be zero only if the transformation squished all of coordinate space onto a single line, or into the origin. 

However, the determinant can actually be negative. What does this mean? It has to do with the idea of orientation. If a transformation seems to flip space over, as if a sheet of paper had been flipped, the determinant would be negative, and this is called **inverting the orientation of space**. In terms of ihat and jhat, jhat always starts to the left of ihat. If after a transformation jhat is on the right, or clockwise from ihat, then space has been inverted. If this happens, the determinant will be negative, and the absolute value of it will still tell you the scaling factor of a given area. 

Why does inverting relate to scaling? As all the areas in coordinate space get squshed as det approaches zero, eventaully all the areas in space become zero and det is zero, and ihat lines up with jhat. After this happens, ihat continues past jhat and the determinant continues to decrease into the negative numbers. 

What about 3D transformations? Instead of telling us the scaling factor for volume, the 3d det tells us the scaling factor for *volume*. The cube that we use for the unit cube is called the **parallelepiped** when a 3d transformation is applied. 

What do negative determinants mean in 3D? We have to use the right-hand rule. If we point our index as ihat, middle finger as jhat, our thumb will be up, representing khat. If we can still do this following the transformation, the determinant is positive. If the relative places of the unit vectors have changed and we can't follow this rule, then the orientation has been flipped and det is zero

## Computing the Determinant
$$
det\begin{vmatrix}a&b\\c&d\end{vmatrix} = ad-bc
$$
Think about what would happen if b and c were zero. Then a would tell you how much ihat is stretched in the x direction, and d would tell you how much jhat is stretched in the y direction. Then it makes sense that ad is the area of the new unit square that used to have an area of one. 

In three dimensions, shit gets complicated. Honestly most people don't need to know how to do this. It's more important to understand what the determinant represents, and how to visualize it. 

$$
det \begin{vmatrix}
a&b&c\\
d&e&f\\
g&h&i
\end{vmatrix}
=
a(ei-fh)-b(di-fg)-c(dh-eg)
$$

## Sources
[Video explanation](https://www.youtube.com/watch?v=Ip3X9LOh2dk&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)