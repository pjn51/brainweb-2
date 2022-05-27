---
aliases: [cross validate, cross validated, k-fold partitioning]
---
# Cross Validation
---
During standard [[model validation]], we only use ~20% of our data to validate our [[modeling|model]]. However, if our [[data]] have pretty high variance, this can skew the results of this validation process. 

We can perform *cross* validation, randomly dividing the training set into $k$ equal sized groups. One at a time, each group acts as the validation set while a fresh model is trained on the other groups of the testing data. By finding the average error across all groups, we can provide a more robust representation of model error. This process is also known as *k-fold partitioning*. 

---
[1]: [[1-14-21 metis]] 