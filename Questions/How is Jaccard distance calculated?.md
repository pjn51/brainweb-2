# How is Jaccard distance calculated?
[[jaccard distance]] is a measure of the dissimilarity of two sample sets. We arrive at the jaccard distance by calculating the *jaccard index* and then subtracting one. The jaccard index is a measure of similarity between sample sets. 
$$
J(A,B) = {{|A \cap B|}\over{|A \cup B|}} = {{|A \cap B|}\over{|A| + |B| - |A \cap B|}}
$$
The above formula is saying that the Jaccard index of set $A$ and set $B$ is equal to the ratio of the intersection to the union of the sets. In other words, sets that have a very large intersection and a very small union will have a high Jaccard index, and therefore a low Jaccard distance. 

For example, let's say we have two sets:

$$
A = [1,2,3,4,5]
$$
$$
B = [3,4,5,6,7]
$$
We can easily see that there is a little bit of overlap between these two sets. We can calculate the Jaccard index by finding the number of observations in both sets, the intersection. We can easily see that there are three observations shared between the sets. We divide this by the total number of observations across the sets, which is ten. Therefore, we arrive at a Jaccard index of 0.3, meaning the Jaccard distance is 0.7. 
$$
J(A,B) = \frac{|A  \cap  B|}{|A\cup B|} = \frac{|3|}{|10|} = 0.3
$$

We've seen how this can be applied to numeric datasets, but it can also be used for [[NLP]] by assigning each word as an observation in the set. 

However, this metric for distance has some limitations.
# [[What are the limitations of Jaccard distance?]]

---
#question/data-science 