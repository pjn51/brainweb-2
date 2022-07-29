# Class Imbalance
`LINKS:` [[2-1-21 metis]]


---
[[Classification requires balanced classes]]. We have to worry about this, because if 99% of the training data is in class A, then a classifier that just put all the predictions in class A would have a 99% [[accuracy]] score. This means that we have to use additional [[metrics]] to grade our models. This is one reason why [[Accuracy is an insufficient classification metric]]. 

We can solve this issue in one of two ways. We can either remove data from the minority class, or we can add data to the minority class in one of a few ways. 

[[To balance classes, undersample, oversample, or create data]]. 

If we already have a *ton* of data, maybe we don't want any more. In that case, we can *undersample* the majority class. 

Else, we should just add data to the minority class. We could just duplicate some observations, through a process called *oversampling*. If that doesn't work, we can create new observations. 

We shouldn't create new observations unless we have to, but we can use a process called [[SMOTE]]. It stands for Synthetic Minority Oversampling Technique. [[SMOTE can balance classes]]. 

We can also try to use something called [[ADASYN]]. This stands for Adaptive Synthetic Oversampling. It tries to find the region where the class imbalance is the biggest issue (usually near a decision boundary) and create new minority observations there. 

It's important to note that we should only oversample the *training data* after we split the test and [[model validation|validation]] data away. 