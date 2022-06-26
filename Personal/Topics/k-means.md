# K-Means Clustering
`TAGS:` 

---
# Introduction
K-Means is probably the most basic [[clustering]] algorithm. We assign *k* random centroids at first, and then the algorithm updates iteratively. Each iteration, each observation is assigned to the nearest centroid based on [[euclidian distance]]. Then, we recalculate the mean observation in each cluster, and re-assign the centroid to that location.

1. Choose *k* centroids
2. Assign points to cluster based on nearest centroid
3. Recompute centroids as mean of cluster
4. Repeat (2) and (3) unti convergence.

By repeating these steps, we can slowly shift the centroids to the actual center of "clouds" of observations. 

We say that this algorithm has *converged* when an iteration yields no movement in any centroid. 

It can be unclear what value we should use for *k*. We have to use our domain knowledge here. We could also use *inertia* to help determine this. Inertia is the sum of squares of distance of points from corresponding centroids, we want to minimize this value, meaning that observations are close to their centroids. This can help grade our clusters in terms of possibly [[accuracy]]. 

Also, unscaled features will be weighted differently in terms of centroid calculation.

# Assumptions
This algorithm assumes that the variance of the distribution of each variable is spherical in however many dimensions the data have. It also assumes that all variables have the same variance, and that each cluster has roughly the same number of observations. This means that [[class imbalance]] can really mess with the results. 

# Strengths
The parameters are really simple. We just have to choose a value for *k.* This is a really fast algorithm, and it's easy to understand what's going on. There's also a guarantee that the results will converge.

# Weaknesses
However, there isn't an obvious way to discern what *k* should be without domain knowledge. We can also get trapped in local minima (to use the concept of gradient descent here). This algorithm is sensitive to outliers, and scaling of the features deeply affects results. 

# Further reading
- [[2-15-21 metis#Lecture - clustering]]