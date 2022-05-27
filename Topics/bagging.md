# Bootstrap Aggregating
`TAGS:`

---
# Introduction
Bootstrap aggregating, or "bagging", is an [[ensembling]] technique. 

We take the training [[data]], and sample it a bunch of times *with replacement*. We end up with a bunch of samples that have repeated entries, and overlap with other samples. 

We take all these samples, and we fit learning models to each of them individually. It's common to fit [[CART models]] to these samples. 

After fitting all the models, we aggregate the results from each model and come to a final prediction. 

One issue with this method is the problem of ==correlated trees==. All the learning models can be really similar if one feature of the data is a good predictor. 

Usually, that's ok. But with this setup, we really want to see all the unique variances within the data, and not just the one that is the most predictive on its own. 

For an additional step that solves this issue, see [[random forest]]. 