---
author: Jason Brownlee
genre: non-fiction
---
# A Gentle Introduction to Bayes Theorem for Machine Learning (2019)
`SOURCE:` [source](https://machinelearningmastery.com/bayes-theorem-for-machine-learning/)
`TAGS:` #wip #article 

---
This is an article about [[Bayes theorem]] and how we can apply it to [[machine learning]] in the form of [[naive bayes]]. 

The author explains that [[Our probabilistic intuition is terrible]] and that we should [[Beware the base rate fallacy]]. 

For example, he says, if we're told that a medical test for cancer has a true positive rate of 85%, we are likely to assume that given a positive result, we have an 85% chance of really having cancer. However, he continues, the real chance we have cancer is only 0.33%!

When we use Bayes' theorem, we can see why. He explains that the base rate is really saying that...

$$
P(\text{positive test} | \text{cancer}) = 0.85
$$However, this *does not mean* that...

$$
P(\text{cancer}|\text{positive test}) = 0.85
$$He says that this is where the base rate fallacy comes from. 

First, we have to determine the probability of a random person having cancer regardless of their test result. We can assume that this is about 0.02%, which is saying that...

$$
P(\text{cancer}) = 0.0002
$$
Using this information, he continues, we can apply Bayes' Theorem. He asks us to remember that this theorem is...

$$
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
$$In this example, he says, $P(A|B)$ is the probability that we have cancer ($A$), given a positive test ($B$). He explains that we have all the information here to begin calculation. 

- $P(A)$ = 0.0002
- $P(B)$ = unknown
- $P(B|A)$ = 0.85

He says that we can estimate the probability of getting a positive test, $P(B)$, in the following way:

$$
P(B)=P(B|A)*P(A)+P(B|!A)*P(!A)
$$Using this, and given the information that the test has a *false postive rate* of 0.05, the author explains that we can find that $P(B) = 0.05$. Note that this is just a coincidence, and the false positive rate isn't precisely determining $P(B)$. 

Finally, he says, we can proceed with the full calculation.

$$
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
$$$$
P(A|B) = \frac{0.85 \cdot 0.0002}{0.05}
$$$$
P(A|B) = 0.0034
$$The article explains that this reveals how terrible the diagonstic test is, even though we would assume that it was relatively trustworthy!

