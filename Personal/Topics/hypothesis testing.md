# Hypothesis testing
`LINKS:` [[statistics]]

---
This is just an entry point into a topic that we would cover far more deeply in the actual bootcamp.

The null hypothesis is the hypothesis that there is no relationship between the things being compared. It is written as $H_0$ 

The alternative hypothesis is the hypothesis that stands in conflict with H0. It is written as $H_a$

The purpose of an experiment is to see if we can reject the null hypothesis, or if we have failed to reject the null hypothesis. This is not the same as accepting $H_0$. 

A one-sided hypothesis test is asking “Is the true value more than the null result?” while a two-sided test asks “Is the true value different from the null result?”

# Types of errors
We can have a false negative (type II), or a false positive (type I) error. Different forms of hypothesis testing have different tendencies to result in one type of error over another. 

# Performing hypothesis testing
We typically try to minimize type I errors, aka we try to prevent false positives. When we talk about a 95% confidence rate, we are saying that there is only a 5% chance of a false positive. 

## Test example
We have a sample of 5 test scores out of a normally distributed population, and we want to determine if the mean score is above 80%. 

First, we define $H_0 = 80$, and $H_a > 80$. 

We will control the type I error rate at 5%. 

We have to calculate a critical region and determine if our sample mean falls outside or inside of this region. If it falls inside the critical region, we can reject $H_0$. 

In order to find this region, we calculate a test statistic. This represents the sample. There are many test [[statistics]] out there that we can use for our problems. We choose which to use based on the population size, and the sample size, and the normality of the population. 

We also need a critical value that will represent the 5% error control from earlier. 

Basically, we assume that the null hypothesis is true. We then represent the [[data and distributions|distribution]] of the probabilities of drawing a [[sample and population|sample]] with a given mean. If it is extremely unlikely that we would draw the sample that we did, then we can reject the null hypothesis. If it is reasonable that in a world where $H_0$ is true that we would pull the sample that we did, we fail to reject $H_0$ . 

In [[Python]], we take the test statistic, and then we plug it into `scipy.stats.t.ppf()`. Inside this function, we first input the confidence level we desire, and second we input the degrees of freedom. The degrees of freedom are calculated by adding the length of both groups, and then subtracting 2. This function gives us the critical value. If this critical value is closer to zero than the test statistic, it means that we can reject the null hypothesis!

If we want to find the probability of observing a difference in sample means greater than the one we found (assuming $H_0$ is true). In order to do this, we run...

`stats.t.cdf(test_stat, deg_freedom)`

This will give us the % chance that the difference in the means of both groups is purely a coincidence, and $H_0$ is still true. If this % is below the alpha, we can reject $H_0$. 

If we just want to find the solution without trouble, we can take a shortcut by using...

`stats.ttest_ind(group_1, group_2)`

This assumes equal variance between both groups, but it will run a T-test really quick, and give you a P-value. 