---

---
*We can create vectors in [[Python]]* using the `ax.quiver()` function and the `plt` library. Since [[Vectors are collections of scalars]], we begin with an array:

```python
arr = np.array([0,0,1,2])
X, Y, U, V = zip(*arr)
```

The above code creates an [[array]], then reverse zips (using `*`) it into a series of [[tuples]]. 

Then we can display the vector using [[matplotlib]] and `ax`. 

```python
plt.figure()
ax = plt.gca()
ax.quiver(X, Y, U, V, angles = 'xy')

plt.draw()
```

---
#idea/compsci 