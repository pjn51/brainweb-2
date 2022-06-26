# Magnitude / vector norm
`LINKS:` [[linear algebra]]

---
# Introduction
Vector norm is a term used in [[linear algebra]]. It is synonymous with magnitude and vector length. 

Norm is a [[function]] that assigns a positive length to each vector. We will be focusing on the Euclidean norm, also known as the magnitude. 

We can generalize the calculation of a magnitude of vector x...

$$||x|| = \sqrt(x_1^2 + x_2^2 + ... x_n^2)$$

This theorem is based on the Pythagorean theorem.

# Calculating norm in [[Python]]
We can use `np.linalg.norm( )` to calculate the magnitude / norm of a vector / array.
We could also use `scipy.linalg.norm( )` to do this.