# Metis Notes for Tuesday, Feb 2nd
`LINKS:` [[metis week 5]]
#meeting/career

---
Today we're starting off with a classification assessment, and then diving into [[data]] visualization, ensembling, and XGBoost. 

## Lecture - [[ensembling]]
For more information, see my `ensemble_methods.ipynb` notebook inside my `onl_ds5` repository. Also remember that we can apply [[pickle]] to whole models.

The goal of ensembling is to provide the combined power of many models. If you were rich, you wouldn't try and have one really amazing lawyer on your legal team, you would have a whole room full of lawyers to advise you. In a similar way, we get a whole heap of models and then *aggregate* their results. 

[[bagging]] is a method of aggregation. Each sample that we get from the data has as many obervations as the overall dataset, but we sample with replacement so that each sample has lots of repeat observations. This means that each sample is slightly different since repeats are not uniform. This method reduces variance and simulates what sampling would really be like if we were sampling from a real population. 

By training a model on each sample that we get from bagging, we can capture all the variance of the population. This means that no matter what sample we get during [[model validation|validation]] or testing, we have at least a few models trained on a similar sample. 

Fundamentally, a model is a set of parameters (like coefficients) and a set of instructions of how to combine those parameters with an input to get an output. When a model has high variance, this means the parameters vary a lot based on whatever input the model is being trained on. 

In order to combat this variance, we can ensemble using multiple models, or even multiple kinds of models. We need a *voting protocol* to aggregate the results of all these models and reach a single output. We can use *weighted voting,* where we take the weighted average between all the models. 

When using weighted voting, we have to determine the weights for each model. There's no standard way to do this, since it depends on what models you're using. One method to do this is called a *stacked classifier.*

A stacked classifier is an ensemble learning technique that combines multiple classification models via a *meta-classifier.* Each model is trained on a subset of the training data, perhaps using bagging. Each model outputs a prediction, and these predictions go into the meta-classifier as the training data. The meta-classifier outputs a final prediction based on the predictions of all the other classifiers. That means the features for this model are the results of all the models that feed into the meta-classifier. For convinience, we can use the `StackedClassifier` object in Scikit-learn. 


| Ensembling Pros          | Ensembling Cons           | 
| ------------------------ | ------------------------- |
| Reduces variance         | Not interpretable         |
| Better model performance | Computationally expensive |
|                          | Possibility of high bias  |

## Lecture -  [[gradient boosting]]
One implementation of gradient boosting is called XGBoost. In this lecture, we're going to cover the mathematics of gradient boosting, some typical use cases, and then the specific XGBoost package.

When we use bagging, we take strong learners and reduce their variance by aggregating many models' results together. *Boosting* is kind of the opposite process. We take a weak learner with high bias ( see [[bias-variance tradeoff]]) and improve the model through ensembling. 

We can iteratively improve the model by running it again and again. Each time we run it, we feed in some information from the previous model to get a little closer to representing all the patterns in the data. 

The most powerful variety of boosting is *gradient boosted trees.* In this variety, each model is a weak learner that is trying to model the *[[residuals]]* from the previous model. Basically, each model is plugging the holes of the previous model. 

We start to run into issues of overfitting if we do this for too many iterations. We can add a *learning rate* that scales the [[residuals]] and only takes some portion of the residuals as information for the next model. This attempts to prevent the model from overfitting. 

We can integrate the concept of [[gradient descent]] with boosting. With gradient descent, we have a loss [[function]] that we can visualize as a curve. We can incrementally crawl along the curve by manipulating model parameters until we reach the minimum of the curve. Every step we take is kind of like modeling the gradient of the [[loss function]]. For a code implementation, see `xgboost.ipynb` in my `onl_ds5` repo. 

| Gradient Boosting Pros     | Gradient Boosting Cons | 
| -------------------------- | ---------------------- |
| High performance           | Complex to tune        |
| Works well with messy data | Not interpretable      |


```python
import xgboost as xgb

gbm = xgb.XGBRegressor(
						n_estimators = 100,
						max_depth = 3,
						objective = 'reg:squarederror',
						learning_rate = 0.1,
						subsample = 1,
						min_child_weight = 1,
						colsample_bytree = 0.8
)

gbm.fit(x_train, y_train)

gbm.score(x_train, y_train)
```


| Hyperparameter     | Description                                            |
| ------------------ | ------------------------------------------------------ |
| `n_estimators`     | number of base learner trees                           |
| `max_depth`        | max depth per tree                                     |
| `learning_rate`    | shrinkage factor applied to each tree update           |
| `objective`        | tells us which loss func to use                        |
| `subsample`        | size of the data subsample per tree                    |
| `min_child_weight` | n of samples in a leaf that will split the tree        |
| `colsample_bytree` | feature subsampling rate, similar to [[random forest]] | 

