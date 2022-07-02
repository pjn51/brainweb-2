---
author: 3Blue1Brown
rating:
genre: STEM
format: video
---
# 3blue1brown: The Binomial Distribution
`LINKS:` [source](https://www.youtube.com/watch?v=8idr1WZ1A7Q)
`TAGS`: #wip #video

---
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/8idr1WZ1A7Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

> [!info]
> This is a video by the 3blue1brown channel dealing with one of the common [[distributions]], the binomial distribution.

Imagine that we're buying something online, the author proposes. He says that one seller has 100% positive reviews, but only 10 of them. He says that the second seller has 50 reviews, with 96% of them being positive, and that the third seller has 200 reviews with 93% postive. He asks us which is the logical choice here. 

The author remarks that we naturally trust situations where there's more evidence, but asks how we can be rational about this. In order to answer this, he asks us what the model is, and what we're trying to optimize. 

He asks us to model sellers as producing random experiences based on probability. In this scenario, one seller might generate 95% postive experiences, while another generates 91% postive. The author proposes that we call the percentage here the *success rate,* or simply S. He says that we want to maximize S.

First, the author poses the challenge of finding the probability of seeing a given sample based on a known value for S. Basically, he asks what the probability of seeing some number of positive reviews in a row is, given that S=0.95, or some other known value. 

The probability of having 48 positive reviews out of 50, given that 0.95 of the reviews are positive, is...

$$ 
P( \text{48 positive}, \text{2 negative} | s=0.95) = \binom{50}{48}(0.95)^{48}
(1-0.95)^2
$$

Let's break this down a little. $\binom{50}{48}$ is called "50 choose 48" and it represents the number of ways in which there could be 50 reviews and we choose 48 of them to be positive. For example, we could have the first two be negative, or the first and third, and so on. For this combination, it equals 1,225. 

To this term, we multiply the probability of seeing any single one of these patterns. We represent this as:

$$
(0.95)^{48}(1-0.95)^2
$$

Since there is a 0.95 probability of any one review being positive, and we have 48 positive reviews, we arrive at $(0.95)^{48}$ as the probability of a review being positive. We multiply this by the probability of a review being negative, which is $(1-0.95)^2$

By changing the values for the positive and negative review counts and holding the positive-review rate constant, we can see which samples are most likely given a certain rate of positive reviews.

The distribution of all these probabilities is known as the [[binomial distribution]]. 

Generalizing the above equation, the author says that we can conclude that the above equation represents the probability of us seeing some data, given a success rate. He says that we want to use this knowledge to determine the probability of a success rate, given the data. He reminds us that while these two things are related, they are distinct. He says that in order to discuss this, we need another video, and points us to his next in the series, [[3blue1brown - Why “probability of 0” does not mean “impossible” (2020)]]. 