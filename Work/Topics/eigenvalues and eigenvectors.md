# Eigenvalues and Eigenvectors
`LINKS`: [[linear algebra]]


---
## Introduction
**Eigenvector**: special vectors that are associated with a matrix. When they are multiplied by a matrix, they produce the same vector but scaled up or down.

**Eigenvalues** correspond with the eigenvector, and determine the level of scaling. 

Each eigenvector corresponds to an eigenvalue, and a matrix of size n by n will have n eigenvalues. 

The general formula is below, where A is an array, x is the eigenvalue, and 𝜆 is the eigenvector. 
		
		$$𝐴𝑥=𝜆𝑥$$

## Use in [[PCA]]
Given some cloud of data, we can reestablish the coordinate system to be aligned with the variance of the data. This makes analysis more efficient. 

## Calculating eigenvectors and eigenvalues
There’s a complicated and confusing way to do this manually.
We can use `scipy.linalg.eig(my_matrix)`. This will return the most powerful eigenvector. 

# According to 3BLUE1BROWN
[Video link.](https://www.youtube.com/watch?v=PFDu9oVAE-g&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=14)
This topic is unintuitive for many students but they're pretty straightforward. The real issue is that it only makes sense if you have a visual understanding of matrices as linear transformations. You also need to be comfortable with other ideas too, but once you do, eigenvectors and eigenvalues aren't that bad.

Consider a linear transformations in 2d that moves ihat to the coordinates 3,0, and jhat to (1,2). We represent this transformation with this matrix...

$$
\begin{vmatrix}3&1\\0&2\end{vmatrix}
$$

Think about what this tranformation would do to some vector, and the span of the vector. Most vectors would be knocked off of their span, since it would be a big coincidence if the vector happened to be on the exact line that it was before (aka most vectors would be pointing a different direction after transformation). But some vectors wouldn't be! Some vectors are unaffected in terms of direction, and are just scaled by a transformation. 

In the above transformation, ihat is such a vector. Ihat just moves along the x axis. Any other vector along the x axis has the same property in this way. These special vectors are called the **eigenvectors** of the transformation. Each eigenvector has its **eigenvalue** which is the factor by which its magnitude changes due to the transformation. 

Consider a 3d rotation. If we can find an eigenvector for the rotation, we would have found the axis of rotation. With any linear tranformation, we cound understand the transformation by looking at the change of the basis vectors. But a deeper way to understand what the transformation is really doing is to find the eigenvalues and eigenvectors. 

Here's the form this takes mathematically...

$$
A\overrightarrow{v}=\lambda\overrightarrow{v}
$$

... where *A* is the transformation matrix, $\overrightarrow{v}$ is the eigenvector, and $\lambda$ is the eigenvalue. 

Finding the eigenvectors and eigenvalues comes down to finding the values of $\overrightarrow{v}$ and $\lambda$ that make this expression true. 

To work with this, let's try and rewrite this equation. Since the left side is matrix-vector multiplication and the right side is scalar multiplication, we should try and get the right side into the matrix-vector form. We can change lambda into a matrix that has lambda down the diagonal, since we are multiplying each basis vector by lambda. The common way to write this is to factor out lambda, and have the matrix be the identity matrix. 

$$
\lambda
\begin{vmatrix}
1&0&0\\
0&1&0\\
0&0&1\end{vmatrix}
$$

Now we can have the equation in this form...

$$A\overrightarrow{v}-(\lambda I)\overrightarrow{v} = \overrightarrow{0}$$

Once we factor out the v...

$$(A-\lambda I)\overrightarrow{v}=\overrightarrow{0}$$

Now we have a new matrix in the parentheses, and we want to find the vector *v* so that the product gives the zero vector. Zero would work for *v* but we want a nonzero vector. 

We should remember that the only way for a nonzero vector product to be zero would be if the [[the determinant]] is zero and space is being squished into a lower dimension. 

Since the determinant changes with lambda, all we have to do is find a value of lambda such that the determinant of the new matrix is equal to zero. Once we've found a lambda that makes this true, we know that the lambda is an eigenvalue of $\overrightarrow{v}$, which is an eigenvector for the matrix *A*. 

To determine the eigenvector, we plug in lambda, and determine which vectors are sent to zero by the transformation. 

A 2D transformation might have no eigenvectors. If it rotates all vectors, it wouldn't have any. If we try to compute one, lambda would resolve as an imaginary number. 

Eigenvalues can be shared by many eigenvectors, or eigenvectors can have unique eigenvalues.

What if the basis vectors are eigenvectors? We would see a diagonal matrix emerge. A diagonal matrix is one in which all the basis vectors are eigenvectors, and looks like a matrix with zeroes everywhere but the diagonal. The numbers on the diagonal are the eigenvalues of each basis vector. Transformations represented by this matrix are just scaling the basis vectors by some number (the eigenvalue). 

It's really convenient for the basis vectors to be eigenvectors. But what if we have some eigenvalues, can we just change the basis vectors from ihat and jhat to these eigenvectors? Yes we can. That is discussed in my note on [[change of basis]].