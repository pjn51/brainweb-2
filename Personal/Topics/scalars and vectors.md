# Scalars and Vectors
`TAGS:`

---
# Introduction
This is a [[linear algebra]] concept. 

# Scalars
[[Scalars are single real numbers]]. 

# Vectors
[[Vectors are collections of scalars]]. 
[[Vectors are used in multiple fields]].
[[Vectors have magnitude and direction]].
[[Vector magnitude can be calculated using the Pythagorean theorem]]. 
[[We can visualize vectors]]. 

## Operations with scalars
[[Scalars and vectors can operate on one another]]. 

## Creating vectors in Python
[[We can create vectors in Python]]. 

# Real coordinate spaces
This is simply a space where real numbers collectively determine points according to some coordinate system. 

Coordinate spaces can be classified according to their dimensions, with the most common conception being a 2d coordinate space (a grid). We define real coordinate spaces by the notation ℝn  meaning that the space consists of all real numbers in n dimensions. 

# Vector Operations
## Vector addition and scalar multiplication
Addition/subtraction of vectors 

$$a + b = (a_1 + b_1, a_2 + b_2, ... a_n + b_n )$$

All the normal rules and properties of addition apply to vector addition. 

EX: adding the vector [0,0,1,4] with the vector [0,0,2,1] would result in a vector of [0,0,3,5]. 

Geometrically, if we want to add vector a to vector b, we just move vector b such that its tail lies at the tip of vector a. The place where vector b now ends is the end point of vector a+b. The start point is the origin of vector a. 

Multiplying a vector by a scalar: 

$$
u*a = |\begin{vmatrix}a_1*u\\a_2*u\end{vmatrix}|
$$

EX: multiplying the vector [2,3] by the scalar 2 would result in a vector of [4,6]
Visually, this doesn’t change the angle of the vector, only changing the magnitude. If the scalar is negative, this will change the direction of the vector to its opposite. 

Geometrically, multiplying a vector by 2 would just stretch it out twice as long without changing the direction. This is called scaling. 

## Linear combinations (operations with vectors)
This is the combo of addition of vectors along with scalar multiplication. 
Remember, this is linear. We don’t use exponentials or polynomials or anything that would make it nonlinear. 

We assume that all vectors are in the set of real numbers and have n dimensions. We also assume that all scalars are real numbers. 

# Span
**Span**: this is the set of all possible vectors that we could reach with a linear combination of a given pair of vectors. $a*\overrightarrow{v}+b*\overrightarrow{w}$ is the span of $\overrightarrow{v}$ and $\overrightarrow{w}$ when *a* and *b* vary over all real numbers. Most vectors have a span including all space, but if the two vectors line up, their span is just the points on the line where they line up. . The vectors could also equal zero, and you would be stuck at the origin.

If we think about two vectors in three dimensions, the span will be a sheet intersecting the coordinate space, since the vectors can't change *direction*. If we add a third vector, the span becomes the whole of the coordinate space. This is assuming that each vector is facing a different direction. 

In the case where a vector is pointing along an axis already included in the span of another vector, that vector is kind of redundant. We could remove it without reducing the span, and we say that these two vectors are **linerally dependent**. If each vector is truly adding a new dimension to the span, we say that they are all **linearlly independent**.

# Basis
We can think about the vector as a combination of some unit vectors and scalars. i-hat is the unit vector in the x direction, while j-hat is the unit vector in the y direction. They each have a magnitude of one, and point directly from the origin along their axis. These two vectors are the *basis vectors* of the xy coordinate system.

When we have a vector of any direction and magnitude, such as [$\begin{matrix}a\\b\end{matrix}$ ], we can think that the x-axis consists of $i-hat * a$, and the y axis consists of $j-hat * b$. 

To complicate things, we could choose different vectors as our basis vectors! This means that the ones we choose are very important, since by choosing specific unit vectors we could cause a vector to reach any point. 

# Zoom out: this is datasci 
We actually use this kind of stuff in [[data science]]. When we develop predictions from a linear regression, we are leveraging a linear combination of features. We will identify the optimal scalars for a certain predictive model. 

Unit vector: a unit vector is a vector with [[magnitude]] of one. These are also referred to as direction vectors. 


