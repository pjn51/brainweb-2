# Clustering
`TAGS:`

---
# Introduction
Clustering is the process of assigning observations to classes during [[unsupervised learning]]. It plays a similar role to classification in [[supervised learning]]. [[k-means]] is the simplest method of clustering. 

We can use *inertia* and the *sillouette score* as metrics to grade our clusters. Inertia is the sum of squared distances from each observation to the centroid. Lower inertia means the clusters are more dense. As we increase the number of clusters, inertia will decrease. But of course we can't just have an infinite number of clusters, since that doesn't tell us anything interesting. This means that when we plot the number of clusters vs the inertia, we look for the *elbow* point. This point represents the happy medium between minimizing the number of clusters and minimizing inertia.
<center>
	<img src='https://miro.medium.com/max/880/1*xOGY4uu6ng7E8lPLP-onWw.png'>
</center>
The sillouette score for a point is a measurement of how much closer it tends to be to members of the same cluster as compared to members of the nearest cluster. A negative score means the point is closer to the points in the neighboring cluster than it is to the centroid of its cluster.  We want to maximize the sillouette score, and really try and avoid negative scores since that indicates overlap between clusters. 

# Choosing an algorithm
We should probably use [[k-means]] as a default, but there are other options that have advantages over k-means. 

![[2-22-21 metis#DBSCAN]]

![[2-22-21 metis#Mean Shift]]

![[2-22-21 metis#Hierarchical Agglomerative Clustering HAC]]

# Related Content

![[2-15-21 metis#Lecture - clustering]]

![[2-22-21 metis#Lecture - advanced clustering algorithms]]

