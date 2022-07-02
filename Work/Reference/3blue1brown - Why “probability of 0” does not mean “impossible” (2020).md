---
author: 3Blue1Brown
rating:
genre: STEM
format: video
---
# Why “probability of 0” does not mean “impossible” | 3blue1brown
`LINKS:` [source](https://www.youtube.com/watch?v=ZA4JkHKZM50)
`TAGS`: #video 

---
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZA4JkHKZM50" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Imagine weighted coin with unknown probability of heads. If ten flips yields 7 heads, can we say that the coin has a 0.7 weight towards heads? Not really. 

If we call this probability of heads *H,* the author says we can ask what the probability that H = 0.7 really is. When we look closer, he informs us that we must expand this 0.7 to 0.700000... to find the real probability that *H* is *exactly* 0.7. 

To the author, the logical conclusion of this train of thought is that for any individual result for *H*, if the probability of that result is not zero, then upon adding these probabilities together, we exceed one and actually arrive at infinity. On the other hand, the author remarks that if the probability of each individual result is zero, then any result is statistically impossible! 

The author says that this paradox has to be escaped from in order for us to work with any continuous variables. He puts forward a possible solution: focusing on *ranges* of possible outcomes, rather than the individual outcomes themeslves. By finding the total area within the range of outcomes, he says that we can approximate the probability of the result lying in that range. He continues, saying that if we then shrink these ranges, we approach a limit at which the probability curve becomes smooth, and each range has an infintely small width. He calls this a *probability density [[function]]*, or PDF, when it is applied to the probability of probabilities.

Contrasting [[discrete and continuous variables]], he says that for discrete variables, the probability of an outcome lying in a given range is the sum of the individual probabilities of each outcome in that range. On the other hand, he notes that when dealing with continuous ranges of outcomes, the situation becomes reversed and the probability of the outcome being in a given range is now the fundamental measure. In this context, he says that the calculation of any individual result becomes the abstraction, and represents finding the area of a space that has no width. In conclusion, he says that we transition from using a sum in the discrete context, to using [[integrals]] in the continuous context. 

To find out how to apply [[probability density function]] tricks to the question of the weighted coin, the author points us to the next video in the series.