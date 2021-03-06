---
aliases: [discrete, continuous]
---
# Discrete and Continuous Variables

---
## Introduction
Discrete and random variables are an important concept to know in [[probability]]. 

A **discrete random variable** is a kind of random variable that can only take on a finite number of values. This basically means it has to be an integer. A dice roll is a discrete variable. 

A **continuous random variable** can be any real number, including floats. Temperature, height, or distance is a continuous variable. 

## Probability Mass Function
This is a func for discrete random vars that indicates the probability of an event is equal to some value. 

When visualized, it’s a histogram of event probabilities basically.

<center>
<img src='https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Discrete_probability_distrib.svg/330px-Discrete_probability_distrib.svg.png'>
</center>

## Cumulative Distribution Function
This func sums the probabilities of the PMF, where we near the value of 1 as we sum the probabilities of more and more possible events. 

![CDF](https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Exponential_distribution_cdf.png/1200px-Exponential_distribution_cdf.png)

## [[probability density function]]
A PDF is for continuous random variables. Since there is an infinite range of possible events, we have to calculate probability density instead of probability directly. We have to calculate the area underneath a section of the curve of the PDF in order to find the probability of the variable falling within that range. 

For example, if we were calculating probable rainfall or temperature, the probability of those values being a specific number would basically be zero, so we have to find the probability of a range. 

![PDF](data:image/png;base64,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)

## Common discrete [[distributions]]
Bernoulli distribution
Binomial distribution
Poisson distribution
- Dedicated to “count data” such as how likely it is for n cars to pass by your house or something. 

## Common continuous distributions
Exponential distribution