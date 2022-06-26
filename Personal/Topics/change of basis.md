# Change of Basis
`LINKS:`[[linear algebra]]
`TAGS:`

---
## BLUE1BROWN explanation
[Video link. ](https://www.youtube.com/watch?v=P2LTAUO1TdA&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=13)

If we have a [[scalars and vectors|vector]] in 2D space, we describe it with coordinates that relate to a set of **basis vectors**. We refer to these basis vectors as *ihat* and *jhat*, and we think of the coordinates as scalars that affect the basis vectors. 

These two vectors encapsule a lot of implicit assumptions in the way we model space. *Ihat* and *Jhat* are the standard vectors for our coordinate system, but we arent't locked into this assumption. 

If we change the basis vectors, we must change the coordinates that we use to locate points and vectors. 

Let's say that we want two new basis vectors, $\overrightarrow{b_1}$ and $\overrightarrow{b_2}$. These vectors are located at (2,1) and at (1-,1), respectively, in the standard system. But from her perspective, those vectors have coordinates (1,0) and (0,1). We're speaking different languages here. The only thing we all agree on is that (0,0) is at the center, and is the origin for vectors. 

### How can we translate between systems? 
We can compute the linear transformation that moves a vector from our system, to a new system. This is just matrix vector multiplication (see [[matrices]]). The matrix represents the basis vectors in our language. 

A matrix whose columns represent the new basis vectors can be viewed as a transformation that we can apply to our basis vectors. We use this to take our misconception of what a different coordinate system is telling us, and allows us to figure out what the coordinates really describe in the alternative system. 

If we want to go the opposite way in transforming, just take the inverse of the transformation matrix. 

### How can we transform vectors in an alternate coordinate system?
Start with a vector in the alt language. Translate the vector into our system using the change of basis matrix. This gives us the same vector in our language. Then transform that vector so that we know where the new one lands in our matrix. Then apply the inverse transformation matrix back into the alt language. 