---
aliases: [classification metric]
---
# Classification Metrics
---
When we want to grade [[classification]] algorithms, we can start simply by looking at the proportion of correct class assignments to the total number of observations. This is [[accuracy]]. If we want to go deeper, we have to introduce the concepts of *true positives, true negatives, false positives, and false negatives.* We will probably want to, since [[Accuracy is an insufficient classification metric]]. 

In some use cases, the number of positives that slip through the cracks is what we want to minimize. For example, If we're building a model that detects cancer cells, we really don't want to miss any. In that case, we should use [[recall]]. 

In other cases, we want to make sure that we're as confident as possible before assigning an observation to the positive category. In that case, we can use [[precision]]. 

See my [[1-27-21 metis#Lecture - classification metrics|lecture notes]]. 