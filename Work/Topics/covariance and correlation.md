# Covariance and Correlation
`TAGS:`

---
# Introduction
In [[statistics]], covariance measures how two variables vary with each other. If two values increase together and decrease together, they have a high degree of covariance. We use covariance to detect relationships between variables. 

We can use `np.cov( )` to find covariance between two variables. 

Covariance is very useful, but it isn’t normalized. If we want to normalize it, we calculate the correlation, which is the covariance scaled by the [[standard deviation]]. This is easier to interpret than covariance. 

We can use `np.corrcoef( )` to calculate this in [[Python]].  

# Autocorrelation
Autocorrelation is the correlation of a pattern with a delayed copy of itself. It is also known as serial correlation. 

We can use this idea to see if a pattern is present in a variable's distribution. For more on autocorrelation in relation to landscape ecology, go [[landscape ecology#Correlation|here]]. 