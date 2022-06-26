# What are the limitations of Jaccard distance?
One thing that really limits [[jaccard distance]] is that it doesn't account for the order of the elements in the sets that are compared. This is especially limiting for [[NLP]]. 

The following sets would have a Jaccard index of 0.44, when in reality they're saying opposite things:
$$
A = [\text{I, don't, like, pasta}]
$$
$$
B = [\text{I, like, pasta, don't, you}]
$$
I'm also not sure how Jaccard distance would function with non-unique sets. For example, would the sets...
$$
A = [1]
$$
$$
B = [1,1,1,1,1,1,1,1,1,1]
$$
...have a high or low Jaccard distance? It would depend on the pre-processing. You would have to remove all repetititions, losing information that way. 

How would Jaccard distance work as the input sizes increase? I'll have to ponder that one. 

---
#question/data-science 