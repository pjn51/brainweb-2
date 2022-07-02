# Linear Transformation
`TAGS`: 

---
This is something in [[linear algebra]] that takes in a [[scalars and vectors|vector]], and spits out a new vector. We say this instead of just saying they're [[functions (python)]] because we want to visualize them a little differently. 

Imagine an input vector and an output vector. We are transforming the input vector so that it is now located at a different end point, and maybe with a different [[magnitude]]. 

We can go further and imagine the set of *all possible input vectors* and *all* of their outputs, but that gets confusing. Instead, let's simplify the input vectors to just be a huge grid of endpoints, and now imagine this grid being warped by the tranformation, and bent in such a way that each grid point moves in a certain way defined by the transformation. 

In LinAlg, we limit these transformations to linear ones. Visually speaking, all lines in a linear tranformation remain straight, and the origin stays in the same place. So don't get too crazy with it! No bending stuff, just tilting it. A rotation is a linear transformation. 

How can we describe these numerically? We want to have the coordinates as our input, and the new coordinates as the output. 

We really just need to keep track of how the basis vectors change, and we can apply this same transformation to any input. 

Any linear transformation can be described as...

$$
\overrightarrow{v} = a*ihat + b*jhat
$$

...where $\overrightarrow{v}$ is the resulting vector, and *a* and *b* are the way that the transformation is changing the unit vectors of ihat and jhat. 

Now that we know where the unit vectors, we know that any vector will land at the coordinates of the vector times the location where the unit vector landed. 

This means that we can totally describe any linear transformation with just two sets of coordinates- the coordinates where ihat lands, and those where jhat lands. It's common to combine these two pairs in a 2x2 [[matrices|matrix]]. 

If ihat lands at (3,-2) and jhat lands at (2,1), we could see a matrix like this...

$$
\begin{vmatrix} 3 & 2 \\ -2 & 1 \end{vmatrix}
$$

If we have this matrix, we can multiply a vector by the matrix to see where the vector ends up! 

To generalize this, what if ihat landed at (a,c) and jhat landed at (b,d). Now we want to see what happens to a vector that has its tip at (x,y).

$$
|\begin{vmatrix} a & b \\ c & d \end{vmatrix}| * |\begin{vmatrix} x \\ y \end{vmatrix}|
$$

The next step...

$$
x * |\begin{vmatrix}a\\c\end{vmatrix}| + y*|\begin{vmatrix}b\\d\end{vmatrix}|
$$

Which simplifes to...

$$
=|\begin{vmatrix} ax+by \\ cx+dy \end{vmatrix}|
$$

Remember, we can also have compositions of multiple linear transformations that are separate from any individual component in the final transformation. 

# Combining Linear Transformations
When we multiply two matrices together, that's like applying one linear transformation, and then another. The composition of the two transformations is the product of the original matrices, which we can think about being the coordinate sets of the unit vectors after a linear transformation. See [this video ](https://www.youtube.com/watch?v=XkY2DOUCWMU&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)for an explanation.

Thinking this way helps us understand why order matters in matrix multiplication. Applying one transformation first is quite different than applying it after another transformation. 

For example, this is how you multiply two 2x2 matrices together. Think of the *columns* as the ihat and jhat, and the rows as the x,y coordinates of the endpoints of those two unit vectors.

$$
|\begin{vmatrix} a & b \\ c & d \end{vmatrix}| * |\begin{vmatrix} e & f \\ g & h \end{vmatrix}|
$$

These matrices are representing two linear transformations of ihat and jhat. We start at the right set of coordinates, and then apply the left transformation.

First, let's think about ihat. ihat is the transformation applied to all x-axis numbers. Therefore, whenever we are trying to find a new x-variable, we need to multiply the old one by the ihat coordinates of the transformation matrix. 

Lets find the composed transformation for ihat. We do this by taking the column *(e,g)*  (which represents the current transformation applied to ihat) and multiplying it my the lefthand matrix. We have to include the lefthand transformations for ihat *and* jhat, since ihat has both horizontal and vertical components to it. 
$$
|\begin{vmatrix} a & b \\ c & d \end{vmatrix}| *|\begin{vmatrix} e \\ g \end{vmatrix}|
$$

We want to find the coordinates for the new ihat, which will lie on the left side of our new matrix. We get this by multiplying the current x coordinate *e*, by the column representing the transformation of ihat, (*ac*). Then, we add the same process for the y coordinate of ihat, represented by *g* in order to find the new y coordinate of ihat. These two terms will be the values in the left side in the new matrix. 

$$
e*|\begin{vmatrix} a \\ c \end{vmatrix}| + g*|\begin{vmatrix} b \\ d\end{vmatrix}| = |\begin{vmatrix}ae+bg\\ ce+dg\end{vmatrix}|
$$

Great! Now we know that in the left side of our composition matrix, we will find the new values that ihat is going to be transofmed by. Let's do the same thing for the right side of the matrix.

We want to find the new transformation that will be applied to the y-axis. We have to start with the first transformation found in the righthand matrix. We look in the right column, the jhat column, (*f,h*). We are going to take this column, and multiply it by the lefthand matrix. 

$$
|\begin{vmatrix}a&b\\c&d\end{vmatrix}|*|\begin{vmatrix}f\\h\end{vmatrix}|
$$

Just as before, we proceed by multiplying the x component of jhat, *f* with the ihat transformation found in the new matrix, the column *(a,c)*. 

$$
f*|\begin{vmatrix} a \\ c \end{vmatrix}| + h*|\begin{vmatrix} b \\ d \end{vmatrix}| = |\begin{vmatrix}  af+bh\\cf+dh  \end{vmatrix}|
$$

These are the new values that will be in the jhat column of our composition matrix.

To put it all together...

$$
|\begin{vmatrix} a & b \\ c & d \end{vmatrix}| * |\begin{vmatrix} e & f \\ g & h \end{vmatrix}|

= 

|\begin{vmatrix} ae+bg & af+bh\\ ce+dg & cf+dh \end{vmatrix}|
$$

# Moving Beyond 2D
Once you've got the 2d way to do stuff down, it's pretty easy to increase the number of dimensions to 3 and even beyond 3. 

When we move into the third dimension, we increase the size of the transformation matrix to have three columns and three rows. We add a new friend of ihat and jhat, called khat. Khat represents the third dimensional component of the transformation. 