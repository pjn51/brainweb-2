---
aliases: []
---
# The Binomial Distribution
---
The binomial distribution is a specific [[probability]] [[distributions|distribution]]. It models the discrete probability distribution of the number of successes in *n* independent experiements, where each experiment has two possible outcomes. 

For example, this is the distribution of the likelihood that a coin flip will result in heads rather than tails over the course of *n* flips. 

$$
P_{(x:\ n, \ p)} = _nC_xxp^x(1-p)^{n-x}
$$
- $n$: the number of trials
- $x$ is the number of "successful" trials (heads)
- $p$ is the probability of successful trial
- $_nC_x$ is the *combination* of $n$ and $x$. A combination represents the number of ways to create a sample of $x$ elements out of the set of $n$ unique elements, where order is irrelevant and there's no replacement. We can represent this as...

$$
_nC_x = \frac{n!}{r!(n-r)!}
$$

---
1. https://www.investopedia.com/terms/b/binomialdistribution.asp#:~:text=The%20binomial%20distribution%20is%20the,possible%20outcomes%3A%20success%20or%20failure.