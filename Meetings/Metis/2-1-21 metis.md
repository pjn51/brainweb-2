# Metis Notes for Monday, Feb 1st
`LINKS:` [[metis week 5]]
`TAGS:` #meeting/career

---
## Pair programming
Our challenge today is to create a [[KNN]] model without using the pre-built functions and objects that we usually do. 

We basically have to take the test and train [[data]] and put them into np.arrays. We have to find the pairwise distances between the testing planets and the training planets, and then use that information to predict which planet is which. 

For more information, see `pair_knn.ipynb` in the `onl_ds5` repo. 

## Ridge office hours
- Hyperparameters overview
	- These are the dials we can manually change to alter our models. 
- KNN hyperparameters
	- *K* is the dial here. As we decrease *k*, the model becomes more sensitive to the data, and tends to move towards overfitting. 
	- As we increase *k*, we start to move towards underfitting the data. 
	- KNN has no cost [[function]], so we have to manipulate *k* as our hyperparameter.
- Precision and recall
	- Some cases make [[precision]] (amount of true vs false positives) more valuable
	- Other cases mean [[recall]] (proportion of actual postives found) is more important
	- In cases where missing a real positive is worse than reporting false positives, we care more about recall. 
	- If a false positive is worse than a false negative, we care more about precision. 

## Lecture - [[CART models]]
By the end of tomorrow, we will have covered all the classification stuff we need for [[fake job classifier]]. The rest of the week will cover visualization and sharing our results. 

CART stands for Classification and Regression Trees. Decision trees are a tool often used for classification based on features. We perform a [[binary]] split based on each features over and over again, making a *tree* of decisions. We refer to each split as a *node* and each final termination point as a *leaf*. These trees are called *decision trees* if we're classifying, and *regression trees* if we're regressing. With regression on continuous features, we just choose a cutoff point to separate which branch to follow.

In order to make predictions using trees, we can just plug in a new observation's features to the tree, and then it will run through all the nodes and come to a final leaf. 

There are some [[hyperparameters]] we need to keep in mind. We can control the number of nodes to use when splitting. If we don't choose enough, we will underfit. If we choose too many nodes, we may overfit (see [[bias-variance tradeoff]]). Overfitting is the main problem with CART models, since they're pretty powerful. 

When we're building a tree, we have to select a feature and make a binary split. We repeat this process until we have a whole tree that fits the data well without overfitting. We split until leaf nodes are pure, with only one class per leaf, or until we reach the minimum number of observations per leaf. We don't want leaves with too few observations in them, so we can limit this manually. 

When we evaluate splits, the model can use some sort of cost funciton to determine which split is best. We can use classification error, which asks how homogenous the observations in each leaf are. We could use some others, but basically we're trying to make the leaves as pure as possible and reduce the chaos in the tree.

In orde to deal with variance, we can use *pruning.* The idea is to let the tree overfit, and then erase some of the splits. We can erase each split if it doesn't increase classification error to do so.

| Pro                            | Con                     |
| ------------------------------ | ----------------------- |
| Easy to interpret              | Overfits easily         |
| Basic logic                    | Difficult to generalize |
| Deals with any data type       |                         |
| Handles missing data well      |                         |
| No scaling needed              |                         |
| Low complexity for adding data |                         |

Now we can get into [[ensembling]]. Why build one tree when you can build a ton? Each model might be kind of bad, but we combine all of them to make them better. We have to use a *bagging* technique.

Bagging stands for Bootstrap Aggregating. It improves robustness by combining *weak learners* into a single *strong learner.* First, we genearte new datasets by sampling uniformly, *with* replacement from the training set. This means that each sample will have a significant amount of overlap with other samples. Then, we fit a learning model to each sample. After each model has been trained, we can run a new observation through all the trees, aggregate their results, and come to a smarter result. This reduces variance without increasing bias, which is pretty sweet. 

Unfortunately, this can result in *correlated trees* if one feature is a much better predictor than the other features. This is an issue because each split will just rely on the single best predictor, losing the information provided by all the other slightly worse predictor features.

## Lecture - [[random forest]]
Random Forest is a method to deal with the issue of *correlated trees* during the bagging process above. 

RF uses a process of *feature bagging.* We want to keep the multiple different models, while considering all the features more equally. To do this, we randomly choose a subset of the features to split on during each split in each tree. This makes sure that each feature has the opportunity to add a little information, influencing the outcome of the model. 

Because of this, RF makes sure that all trees are decorrelated before aggregation. 

There are some guidelines we need to follow for RF. We should use between 50 and a few hundred trees. We don't have to worry about pruning like we would with a single tree, since overfitting in any one tree is okay. At each split, we should consider $\sqrt{m}$ features, where $m$ is the total number of features. If we're doing regression, we should instead consider $m/3$ features during each split. 

We can [[model validation|validate]] the number of trees in the forest, we can use *out-of-bag error*. This measures tree error on samples that aren't included in the training of that specific tree. By plotting OOB error against the number of trees, we can see the optimal number of trees to have. 

One drawback to RF is the loss of interpretability. Since we have so many trees, it's harder to tell which features were inportant. But we can still try and figure this out using global feature influences. But we can't take these values too seriously, and they should only be compared relatively with one another. The absolute numbers themselves don't mean much. 

| Pros                            | Cons                       |
| ------------------------------- | -------------------------- |
| Any data type                   | Less interpretable         |
| Missing values used well        | Poor with categorical vars |
| Few hyperparameters             | XGboost is  better         | 
| Can handle small n obs          |                            |
| Well suited for parallelization |                            |
| Good for tight deadlines        |                            |
| Handles wide datasets           |                            |

## Lecture - Extra Trees method
- "Extremely Randomized Trees"
- Instead of bootstrapping, this method randomizes the cutoff points for the features. 

## Lecture - [[class imbalance]]
- Data with a ton of observations of class A and virtually none for class B is *imbalanced*. 
- The metric trap
	- When your data is imbalanced, the classifier might just predict all the data as class A, and say that you have 95% [[accuracy]]. This is a lie!
	- This is why accuracy is a shitty metric when the data isn't balanced. 
- Train-test-split for imbalanced data
	- Always make sure to use the argument `stratify= <target>`, using your target feature. This will ensure that a representative amount of each target class gets into each group. 
- ==Oversampling==
	- This method is to stretch the tiny class to be equal to the majority class. 
	- We just duplicate the observations of B until we have equal amounts of A and B. 
- ==SMOTE==
	- [[SMOTE can balance classes]]. 
	- Synthetic Minority Oversampling Technique
	- We create additional datapoints that didn't exist.
	- We start by finding the KNN, and randomly picking a point on the line between a point and its nearest neighbor for a new point for the minority class. 
- [[ADASYN]]
	- Adaptive Synthetic Oversampling
	- Like SMOTE but it finds the regions where the imbalance is strongest, and creates new points in those regions.  
- ==Undersampling==
	- We can take the majority class and shrink it.
	- This is better when we have a ton of data and don't want any more. 
	- Basically oversampling in reverse. 
- Deciding on a method
	- First thing to try is *nothing*. Just see if it works without messing with it.
	- If you have a *ton* of data, undersample. Else, oversample in some way. 
	- If that doesn't work, try SMOTE or ADASYN. 
	- If nothing works, try an anomaly detection algorithm. 
- Final note
	- Only oversample the training data!!! 
	- Do the oversampling after you split to avoid *data bleed* between training and testing sets. 