# Metis Notes for Monday, Feb 8th
`TAGS:` #meeting/career

---
We're starting the beginning of [[metis week 6]] with a pair session, followed by a lecture on GLM, and a review of the classification test we took last week. 

## Pair
Our pair today isn't a programming exercise. Instead, we are comparing models based on a few criteria. 

For each question below, say yes, no or somewhat for these classification algorithms: KNN, Logistic Regression, Decision Tree, Random Forest and Naive Bayes.

```
1) Is it interpretable?
2) Is it inherently multi-class?
3) Is it scalable with large number of features (in terms of execution time and quality of results)?
4) Is it scalable with large number of data points (in terms of execution time and quality of results)?
5) Is it good with a diverse (non-homogenous) set of features?
```

KNN
1. Yes it is interpretable
2. It can be used with many classes
3. Yes it is scalable with lots of features (linear complexity)
4. Somewhat (train-time different from test-time)
5. No, all data must be numeric. 

[[logistic regression]]
1. Yes, it is interpretable.
2. No, must be a [[binary]] class.
3. Yes. 
4. Yes, it has less than linear time complexity.
5. No, all data must be numeric. 

Decision Tree
1. Somewhat interpretable
2. Yes. 
3. No. You must compare all the features at each node.
4. Yes.
5. Yes. 

Random Forest
1. Not at all.
2. Yes
3. Yes. Only a subset of the features are compared at each node
4. Yes.
5. Yes. 

Naive Bayes
1. ...
2. Yes.
3. Linear time complexity.
4. Linear time complexity. 
5. No. Everything has to be numeric. 

## Lecture - [[GLM]]
- GLM stands for Generalized Linear Models
- For this lecture, try and use these ideas to help you understand linear models a little better. 
- Linear component
	- We should be familiar with the linear part of a regression problem. 
	- We can call the linear component *z*. 
	- We need to link the target *y* to the linear component somehow. 