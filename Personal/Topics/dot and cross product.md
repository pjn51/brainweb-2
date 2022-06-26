# Dot and Cross Product
`LINKS:` [[linear algebra]]

---
## What is the dot product?
This is one of the two ways to multiply [[scalars and vectors|vectors]] in [[linear algebra]]

We can take two equal-length sequences of numbers and return a single product. 
Geometrically, 

$$a * b = ||a||*||b||*\cos(\theta)$$

where theta is the angle between the vectors.
Algebraically, 

$$a\cdot b = \sum{a_i*b_i} $$

$$a \cdot b = a_1*b_1 + a_2*b_2 + ... + a_n*b_n$$

## Calculating angles between vectors (similarity)
Often, we will need to compare two different things. These might be two different features of a dataset, or something like that. We want to see how similar these relationships are to one another. We can do this by representing these two things as vectors, and then finding how many degrees the vectors are separated by. If they have only a few degrees of separation, they are more similar to one another.

We start by representing both things as arrays in [[Python]]. Then, we take the dot product of the two arrays.

```
a = np.array([4,3])
b = np.array([1,2])
np.dot(a,b)
```

On top of this, we add a layer of complexity. Remember the above equation that involves $\theta$. Theta is what we want to find here, so we apply that to the code above. 

```
math.degrees(math.acos(np.dot(a,b) / (math.sqrt( np.dot(a,a)) * math.sqrt(np.dot(b,b)))))
```

We are basically solving for theta in degrees from the geometric representation of the dot product above. 

## Properties of vectors in regards to dot product
1: If a and b are two vectors such that $b = c*a$ and c is a positive real number, then these two vectors would have a theta ($\theta$) of 0 degrees, meaning that they are very similar. 

2: If the angle between the two vectors is 180 degrees, these vectors would have opposite correlations. This is the opposite of situation 1. 

3: a and b could be perpendicular. We would say these vectors are independent and have no correlation. 

Orthogonality generalizes the idea of perpendicular to n dimensions. Two vectors are orthogonal if their dot product is equal to zero, or one of the two vectors is itself equal to zero. 

## Cross Product
This is less common than the dot product, but you may see it sometimes.
Algebraically, we are taking vectors in from a 3d space. It returns a vector that is perpendicular to the two vectors given. 

a x b =

i | j | k
:------| ------ | ------------:
a1 | a2 | a3
b1 | b2 | b3

$$a \times b = [𝑎2*𝑏3 − 𝑎3*𝑏2, 𝑎3*𝑏1 − 𝑎1*𝑏3 ,𝑎1*𝑏2 − 𝑎2*𝑏1]$$

Another way to think about it is if we use the xyz coordinates... If we say that vector c is the cross product vector, we can say that...

$$c_x = (a_y * b_z)  -  (a_z * b_y)$$
$$c_y = (a_z * b_x)  -  (a_x * b_z)$$
$$c_z = (a_x * b_y)  -  (a_y * b_x)$$

This may seem arbitrary, but there is a method to the madness. We are leveraging the concept of determinants from the matrix. 

Geometrically, the cross product is the same as the product of the two vectors’ length, times the sin of the angle between the vectors. 

$$||a \times b|| = ||a|| * ||b|| * sin(\theta) * n$$

Where ||a|| and ||b|| are the magnitudes of those vectors, theta is the angle between the vectors, and n is the unit vector at right angles to both b and a.

As opposed to a dot product, cross products are maximized when the two vectors given are perpendicular and therefore theta is 90 degrees. 

We use a cross product when we need interactions between different dimensions. 

The result of a cross product will be a 3d vector. The cross product can only operate in exactly 3 dimensions. 

### Angles between vectors
Two vectors that have 0 degrees between them will have a cross product of magnitude zero.

A 180 degree difference will also result in a cross product of magnitude zero.
Two perpendicular vectors will have a cross product equal to$$ ||a||*||b||$$

# Dot product according to 3BLUE1BROWN
[Video link.](https://www.youtube.com/watch?v=LyGKycYT2v0&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)

If we have 2 vectors of the dimension, meaning that 2 lists of numbers with the same length, we can pair each coordinates and multiply the pairs. After we add the result, we got the dot product. 

$$
\begin{vmatrix}
1\\2
\end{vmatrix}

\cdot

\begin{vmatrix}
3\\4
\end{vmatrix}

=

1*3+2*4
$$

This has a nice geometric interpretation. The closer the two vectors are to each other in direction, the larger the dot product will be. Perpendicular vectors have a dot product of zero. Order doesn't matter in this operation. 

Why does the adding of coordinates have anything to do with the geometric view?

To answer this, we have to answer a deeper question, related to linear transformations between 2d and 1d. These are functions that take in a vector and spit out a number. However, they are more restrictive than functions because the transformation has to be *linear*. Points that are evenly spaced in the input space will be evenly spaced in the output space, even if the space has fewer dimensions. 

The linear transformation can be tracked by tracking ihat and jhat. The end result of a linear transformation from 2d to 1d will take the form of a 1x2 matrix. The matrix...

$$
\begin{vmatrix}
2&1
\end{vmatrix}
$$
...is telling us that ihat ends up at position 2, and jhat lands at position 1 on the number line, which is now the whole of coordinate space. 

If we want to follow where a certain vector ends up, we can use the location where the unit vectors land to figure out where the vector ends. By multiplying the transformation matrix by this vector, we find the new location. For instance, if we want to find out where the vector ending at coordinates (4,3) ends up based on the above transformation, we perform...

$$
\begin{vmatrix}
2&1
\end{vmatrix}
*
\begin{vmatrix}
4\\3
\end{vmatrix}
=
4*2+1*3 = 11
$$

This is just like taking the dot product of two vectors, isn't it? By tilting the numberical representation of a vector on its side, we get a 1x2 matrix, and vice versa. 

This relationship is an example of **duality**, a natural but surprising correspondence between two seemingly unrelated things. 

# Cross product according to 3BLUE1BROWN
[Video link.](https://www.youtube.com/watch?v=eu6i7WJeinw&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&t=1)

If we have two vectors in 2d space, think about the shape made by the span of the 2 vectors. (For example, the span made by ihat and jhat is a 1 by 1 square with the corner at the origin). 

The cross product of the two vectors is the area of this parallelogram! Almost. We have to consider orientation. If vector v is on the right of vector w, the cross product is positive, and if its on the left, cross product is negative. This means that order matters in this operation. 

Remember this by remembering ihat x jhat is positive, and ihat is naturally said before jhat, and ihat is on the right of jhat. 

Here's how we calculate the cross product for two vectors, $\overrightarrow{v} = \begin{vmatrix}3\\1\end{vmatrix}$
and 
$\overrightarrow{w}=\begin{vmatrix}2\\-1\end{vmatrix}$, we can calculate the cross product...

$$
det
\begin{vmatrix}
3&2\\
1&-1
\end{vmatrix}
$$
...like that. 

A matrix whose columns represent $\overrightarrow{v}$ and $\overrightarrow{w}$ really represents the linear transformation that moves the basis vectors to the locations of the vectors. 

SInce the determinant measures how areas of space change due to transformations, and the typical area we look at is the unit square, that square gets turned into the new area we want to find the area of for the cross product. 

The cross product increases with the magnitude of the vectors involved (obviously) and also when the vectors are perpendicular to one another. This creates a shape that looks less and less like a diamond, and more and more like a square or rectangle, increasing the area. 

If we scale one of the vectors by, say, three, the area of the span increases by a factor of three as well. 

But wait, the cross product isn't a number, it's a vector! How can this be? Well, the cross product is really a vector that has the magnitude of the area we just found. The direction is perpendicular to the parallelogram, and follows the right hand rule, with the cross product being the thumb. 