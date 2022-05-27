# Independence
`LINKS:` [[probability]]
`TAGS:`

---

When events are independent of one another, the [[probability]] of both happening can be found through multiplication of the individual probabilities. 

#### Example 1
What's the probability of throwing a die 6 times and getting 1 through 6 in order?
P(E) = P(1)*P(2)...*P(6) = 1/46656

#### Example 2
The probability of blinking in a photo is 0.1. If a photo of five people is taken, what's the probability of nobody blinking, at least one person blinking, or everyone blinking?

P(no blinkers) = $0.99^5$
P(one blinker) = $0.1*5$
P(all blinking) = $0.1^5$

## Conditional probability
When one event influences the likelihood of a second event happening, the two events are dependent. For instance, if you draw two cards without replacing the first one, you’ve changed the probabilities involved in the second draw slightly. The outcomes of the two draws are dependent on one another.

P(A and B) = P(A | B) * P(B)

This is saying that the probability of A and B happening is equal to the probability of A happening given B already happened, times the probability of B.

#### Example 3
If a bag has 5 red balls, 3 blue, and 4 green, and we take 2 without replacement, what’s the probability that the first will be green and the second will be blue?
A: P(B and G) = P(blue | green) * P(G). Therefore, P(B and G) = 3/11*4/12. \
