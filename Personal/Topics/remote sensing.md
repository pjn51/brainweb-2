# Remote Sensing 🛰
---
Remote sensing is the science of detecting variables at a distance. [[Remote sensing decodes spectral data]], providing insights into the material measured based on reflectivity at various wavelengths. It's often leveraged in [[environmental science]]. 

# History
It all began with the [[Landsat program]]. NASA pointed a sattelite downward with a camera on it. 

# Collection
[[LiDAR]] is a cutting-edge technique for detailed [[data]] collection that can provide millimeter resolution. 

# Analysis
The primary task of remote sensing is [[classification]], either  [[supervised learning|supervised]] or [[unsupervised learning|unsupervised]]. 

1. Unsupervised techniques
	1. [[k-means]]. 
	2. [[IsoData clustering]]
2. Supervised techniques
	1. Parallelepiped (N-dimensional density slicing. We need ground-truth [[data]] to determine a starting point for classification)
	2. Minimum distance classification (This is kind of like K-means, but we determing the info classes first)
	3. Maximum likelihood classification (Same as min. distance, but variance is also considered)
	4. IsoData supervised
	5. Bayes classification (We can use statistical [[probability]] related to abundance of cover type. This one is controversial)