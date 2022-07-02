---
author: 3Blue1Brown
genre: non-fiction
---
# Solving wordle using information theory (2022)
`SOURCE:` https://www.youtube.com/watch?v=v68zYyaEmEA
`TAGS:` #wip #video 

---
The author asks if there is a [[Data can be quantiative or qualitative|quantitative]] score we can give an opening word in Wordle, that judges the quality of each letter, as well as its placement, assuming that all ~12,000 valid words have an equal possibility of being the answer. 

He makes the interesting point that for something to be informative, it has to be unlikely. This sounds questionable at first, but I think it makes sense. The knowledge that a fact is true only exists relative to the possibility of it being false. Interesting to see how [[Opposites require each other]] here. 

The author constructs a histogram displaying the probability of each unique *combination of clues* being revealed if we play a given word. If we get all grey, that's one combination of clues. If we get the third tile green, and the fifth tile yellow, that's another, etc. That's interesting, and I never thought of doing that when I was trying to make a wordle solver. 

He says that the standard unit of information is the bit. He defines bit as a piece of information that divides the *space of possibilities* in half. Elaborating, he says that we can define information ($I$) relative to the probability of an individual clue pattern being seen ($p$): 

$$
I = \log_2(\frac{1}{p}) \ \text{ or } -\log_2(p)
$$

Basically, he explains, the less likely the clue is to appear (the lower the probability), the more bits of information we gain upon its appearance. He develops a metric that encapsulates the value of each clue combination:

$$
E[I] = \sum p(x) \cdot -log_2(p)
$$

Using this metric, he says we can build a histogram of the information that we might recieve when playing a given word. When that histogram tends towards the right, and we are likely to gain a decent amount of information when playing that word, then the word has a good score on our metric. He explains that this metric is called *entropy.* 

