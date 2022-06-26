# Matrix Inverse & Systems of Equations
`LINKS:` [[linear algebra]]

---
This is a concept related to [[matrices]] and, more generally, [[linear algebra]]. 

To understand the inverse of a matrix, we need to understand what matrices are used for. LinAlg is so broadly applicable because it lets us solve systems of equations. 

The most basic system of equations is one in which each term is just a scalar and a variable, all added together, such as this one...

$$2x+5y+3z=-3$$
$$4x+0y+8z=0$$
$$1x+3y+0z=2$$

We can rewrite this as a matrix.

$$
\begin{vmatrix}2&5&3\\4&0&8\\1&3&0\end{vmatrix}*\begin{vmatrix}x\\y\\z\end{vmatrix} 

= \begin{vmatrix}-3\\0\\2\end{vmatrix}
$$

We can name the constant matrix *A*, the variable vector $\overrightarrow{x}$, and the result vector $\overrightarrow{v}$. 

This means we can write the system as $A\overrightarrow{x}=\overrightarrow{v}$. This is a lot simpler than trying to keep all the above in your head. 

The idea of a **matrix inverse** is that the inverse of matrix *A* is the transformation that, when applied to the transformation found in *A*, will get us back to the standard location of the unit vectors. This standard location of the unit vectors is known as the **identity matrix**.

Alegbraically, this means that the inverse of *A*, called $A^{-1}$, is such that $A*A^{-1}=I$, where $I$ =

$$
\begin{vmatrix}1&0\\0&1\end{vmatrix}
$$

We can use this inverse matrix to cancel a matrix out. It's basically like dividing by a matrix. 

Now, we can apply this concept to the system of equations we talked about earlier, $A\overrightarrow{x}=\overrightarrow{v}$. 

If we multiply both sides by $A^{-1}$, we come to a new equation, which we can write as $\overrightarrow{x}=A^{-1}\overrightarrow{v}$.

It's important to note that for a matrix to have an inverse, it has to have a non-zero determinant. If det = 0, then space will be squished into a smaller dimension, and we can't unsquish something into a higher dimension. However, we still might be able to find a solution when A is not invertible. We just have to be lucky and hope the vector v lives somewhere in the area that space is now squshed into. 

You might note that having a zero determinant can mean that coordinate space is being squished onto a plane, or onto a line. This makes for very different outcomes in terms of how likely we are to have vector v in that space, so we have more specific terminology to describe this. 

If the transformation results in a 1D space, we say that the **rank** is 1. If the new space is 2D, we say the rank is 2. The word rank really means the number of dimensions in the output of a transformation. 

The set of all possible outputs $A\overrightarrow{v}$ is called the **column space** of *A*. This name comes from the columns of the matrix, where the columns tell you where ihat and jhat land. The span of these two vectors tell you the whole of column space. 

A more precise definition of rank would be the number of dimensions in the column space. We say a matrix is *full rank* when dimensionality isn't decreased at all. For a full rank matrix, only one vector lands on the origin, since the origin is fixed during a linear transformation by definition. However, when rank is not full, more than one vector could land on 0,0. This is because the number of dimensions has decreased. 

The area of vectors that land on the origin is called the **null space, or kernel** of the matrix. 