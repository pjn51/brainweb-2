---
aliases: [matrix]
---
# Matrices
---
A matrix is a 2d array of numbers that is important in [[linear algebra]]
We think of matrices as having a shape of $M \cdot N$ with $M$ rows and $N$ columns. We use $i$ and $j$ to denote rows in the form $i,j$  to say that we’re talking about the value at row $i$ and column $j$.

[[There are a few common matrices]] that have useful attributes. 

# Matrix Operations with [[scalars and vectors]]
[[Scalars are single real numbers]]. 
When multiplying a matrix by a scalar, it follows the same rules as with any array. 
When multiplying a matrix by a vector, you have to make sure the dimensions are compatible with one another. 

## Matrix operations with scalars
We can add, subtract, or multiply a scalar and a vector easily enough. We just do this on an element by element basis.

$$
\begin{vmatrix}x_1 & x_2\\x_3 & x_4 \end{vmatrix} * a = \begin{vmatrix}x_1*a & x_2*a\\x_3*a & x_4*a \end{vmatrix}
$$
### Matrix operations with vectors
$$
\begin{vmatrix}
x_{11} & x_{12} & ... & x_{1n}\\x_{21} & x_{22} & ... & x_{2n}\\...& ...& ... & ...\\x_{m1}&x_{m2}&...&x_{mn}

\end{vmatrix} * \begin{vmatrix}u_1 \\ u_2 \\...\\u_n \end{vmatrix}

=

\begin{vmatrix} x_{11}*u_1 & x_{12}*u_2 & x_{13}*u_3 & ... & x_{1n}*u_n \\ x_{21}*u_1 & x_{22}*u_2 & x_{23}*u_3 & ... & x_{2n}*u_n \\ ... & ... &...&...&...\\ x_{m1}*u_1 & x_{m2}*u_2 & x_{m3}*u_3 & ... & x_{mn}*u_n \\
\end{vmatrix}
$$
Note that the vector has to have a length *n* equal to the width of the matrix for this to work. 
# Mathematical Operations with Matrices and other Matrices
We can add or subtract two arrays with the same shape fairly easily. 

*I don't have a good understanding of this either.*

# Linear Transformations
We can apply linear transformations by thinking of a matrix as our transformation matrix that will be applied to something. 

# Other Operations
## Transpose
We can transform the rows into columns and the columns into rows, using the `.transpose()` method of an array.

When taking the dot product of two matrices, transposing the final result is the same as transposing the two inputs before the product is taken. 

## Determinants
They are denoted as det(A) for a determinant of matrix A.
We use determinants to check if a matrix is invertible. 
For a 2x2 matrix...
$$
det \begin{vmatrix}a1 & a2 \\ 
a3 & a4 \end{vmatrix}
= a1*a4 - a2*a3$$

For a 3x3 matrix, it’s a little more confusing. We take the elements from the top row, and multiply them by all lower elements not in their column.

$$
det \begin{vmatrix}a1&a2&a3\\
a4&a5&a6\\
a7&a8&a9 \end{vmatrix}
=
a1 * \begin{vmatrix}a5&a6&a8&a9 \end{vmatrix} - a2*\begin{vmatrix}a4&a6&a7&a9 \end{vmatrix} - a3*\begin{vmatrix}a4&a5&a7&a9\end{vmatrix}
$$

Of course, solving for this programmatically is much easier. We can just use the scipy library by calling ` linalg.det(matrix_name)` or numpy by calling `np.linalg.det(matrix_name)`. 

We will need these determinants for solving for [[eigenvalues and eigenvectors]]. 
We cannot solve for the determinant of a non-square matrix. 

See more on what [[the determinant]] really means here. 

# Matrix Multiplication Geometrically
When we multiply two matrices together, that's like applying one linear transformation, and then another. The composition of the two transformations is the product of the original matrices, which we can think about being the coordinate sets of the unit vectors after a linear transformation. See [this video ](https://www.youtube.com/watch?v=XkY2DOUCWMU&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)for an explanation.

Thinking this way helps us understand why order matters in matrix multiplication. Applying one transformation first is quite different than applying it after another transformation. 

For example, this is how you multiply two 2x2 matrices together. Think of the *columns* as the ihat and jhat, and the rows as the x,y coordinates of the endpoints of those two unit vectors.

$$
\begin{vmatrix} a & b \\ c & d \end{vmatrix} * \begin{vmatrix} e & f \\ g & h \end{vmatrix}
$$

These matrices are representing two linear transformations of ihat and jhat. We start at the right set of coordinates, and then apply the left transformation.

First, let's think about ihat. ihat is the transformation applied to all x-axis numbers. Therefore, whenever we are trying to find a new x-variable, we need to multiply the old one by the ihat coordinates of the transformation matrix. 

Lets find the new value for ihat. We do this by taking the column *(e,g)*  (which represents the current transformation applied to ihat) and multiplying it my the lefthand matrix. We have to include the transformations for ihat *and* jhat, since ihat has both horizontal and vertical components to it. 
$$
\begin{vmatrix} a & b \\ c & d \end{vmatrix} *\begin{vmatrix} e \\ g \end{vmatrix}
$$

We want to find the coordinates for the new ihat, which will lie on the left side of our new matrix. We get this by multiplying the current x coordinate *e*, by the column representing the transformation of ihat, (*ac*). Then, we add the same process for the y coordinate of ihat, represented by *g* in order to find the new y coordinate of ihat. These two terms will be the values in the left side in the new matrix. 

$$
e*\begin{vmatrix} a \\ c \end{vmatrix} + g*\begin{vmatrix} b \\ d\end{vmatrix} = \begin{vmatrix}ae+bg\\ ce+dg\end{vmatrix}
$$

Great! Now we know that in the left side of our composition matrix, we will find the new values that ihat is going to be transofmed by. Let's do the same thing for the right side of the matrix.

We want to find the new transformation that will be applied to the y-axis. We have to start with the first transformation found in the righthand matrix. We look in the right column, the jhat column, (*f,h*). We are going to take this column, and multiply it by the lefthand matrix. 

$$
\begin{vmatrix}a&b\\c&d\end{vmatrix}*\begin{vmatrix}f\\h\end{vmatrix}
$$

Just as before, we proceed by multiplying the x component of jhat, *f* with the ihat transformation found in the new matrix, the column *(a,c)*. 

$$
f*\begin{vmatrix} a \\ c \end{vmatrix} + h*\begin{vmatrix} b \\ d \end{vmatrix} = \begin{vmatrix}  af+bh\\cf+dh  \end{vmatrix}
$$

These are the new values that will be in the jhat column of our composition matrix.

To put it all together...

$$
\begin{vmatrix} a & b \\ c & d \end{vmatrix} * \begin{vmatrix} e & f \\ g & h \end{vmatrix}

= 

\begin{vmatrix} ae+bg & af+bh\\ ce+dg & cf+dh \end{vmatrix}
$$

# Nonsquare Matrices
It makes sense to talk about transformations between dimensions, like taking a 2D vector to the 3rd dimension. As long as the origin stays in the same place and gridlines are parallel, we don't have a problem. 

In a 3x2 matrix, the 2 columns are still ihat and jhat, and the three rows correspond to the three coordinates where the unit vector ends after the transformation. This means that we are taking an input that has two dimensions, and moving it into three-dimensional space. 

For a 2x3 matrix, we are starting with three basis vectors (3d space) and we are ending in a spot that is described with only two coordinates. This is a transformation from 3d space to a 2d plane. 

A transformation could take place from 2d space to 1d space (a number line). These transformations are written using 2x1 vectors. 