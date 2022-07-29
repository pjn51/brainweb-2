# Finding needles in haystacks is hard.
For example, let's look at a super powerful terrorist-finding algorithm and see how well it really works. To do this, we need to use [[Bayes theorem]]:

$$
P(T|S)=\frac{P(S|T)* P(T)}{P(S)}
$$

We want to find the probability that a person is a terrorist, $P(T)$, given that our 99% accurate terrorist finder algorithm selected them, $P(S)$.  We want to find $P(T|S)$. 

If 99% of the terrorists are found by the algorithm, $P(S|T)=0.99$. However, there are extremely few actual terrorists in the population, and $P(T)=0.00001$. This is saying that only 0.0001% of the population are terrorists, which would amount to 3,310 terrorists in the US, which is very generous. 

First, we need to find $P(S)$, the probability that a random person would be selected by the algorithm. We can find this by using the following equation:

$$
P(S)=P(S|T)*P(T)+P(S|!T)*P(!T)
$$
We have to be given the *specificity* of the tool, which represents the proportion of true negatives, times in which the algorithm correctly declares someone as *not* a terrorist. Let's assume that the algoritm is able to do this 99% of the time. 

We can use the following values:
- $P(S|T)=0.99$
- $P(T)=0.00001$
- $P(S|!T)=0.01$
- $P(!T)=0.99999$

Using these values, we can find that...

$$
P(S)=0.99*0.00001+0.01*0.99999=0.01
$$

Now we can proceed to find the probability that somebody is actually a terrorist given that they've been selected as one:

$$
P(T|S) = \frac{0.99*0.00001}{0.01}=0.00099
$$

This means that given an algorithm that selects 99% of the terrorists, and only selects non-terrorists 1% of the time, there's only a 0.01% chance that the person who just got selected is actually a terrorist!

Our inability to grasp this is called the base rate fallacy ([[Beware the base rate fallacy]]). 

---
#idea/math/probability 