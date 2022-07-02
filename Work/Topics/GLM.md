# Generalized Linear Models
`TAGS:` 

---
## Introduction
Generalized Linear Models, or GLMs, are a flexible generalization of [[linear regression]] [[modeling]] methods. They allow for dependent variables that have error [[distributions]] other than the [[normal distribution]]. The GLM allows the linear model to use a link function and by allowing the magnitude of thevariance of each measurement to be a function of its predicted value. 

## Advantages over linear regression
Ordinary linear regression assumes that a constant change in a feature or features results in a constant change in the target feature. However, these assumptions are violated for some use-cases. 

For example, if a linear regression is trained on beach attendance, it may find that a 10-degree increase in temperature results in 1,000 more beachgoers on [[average]]. This model would fail to take into account the average beach attendance, and would always predict 1,000 more beachgoers if the temperature increased by 10 degrees, no matter the size of the beach. 

A more realistic beach model would instead predict a constant rate of increased beach attendance, and would predict that a 10-degree increase leads to a doubling in beach attendance, for example. This sort of model would be called an *exponential-response model,* or a *log-linear model*. 

If we are trying to predict a probability of making a binary choice, then a linear response model is even less suitable, since probabilities are bounded at 0 and 1. If we are trying to relate temperature with the likelihood of someone going to the beach, we could say that a 10-degree increase leads to a doubling in the odds that someone will go to the beach. This would be called a *log-odds model* or *logistic model*. 

## General form
Each outcome $Y$ of the dependent variable is assumed to be generated from a particular distribution in an exponential family, which includes distributions such as the normal distribution, binomial distribution, and the Poisson distribution. 

The mean of the distribution, $\mu$, depends on the independent variable, $x$, through this function...

$$
E(Y|X)=\mu=g^{-1}(X\beta)
$$

...where $E(Y|X)$ is the expected value of $Y$ conditional on $X$. $X\beta$ is the linear predictor, and $g$ is the link function. 

## Model components
The GLM consists of three elements:
1. An exponential family of probability distributions
2. A linear predictor
3. A link function

## Further reading
For an extremely brief introduction, see my [[2-8-21 metis]] notes.