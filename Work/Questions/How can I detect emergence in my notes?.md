# How can I detect emergence in my notes?
One huge advantage of a [[zettelkasten method|Zettelkasten]] is that I can see emergent connections between ideas. After all, [[Emergent associations beat predetermined categorization]]. However, I think this process has a scale issue. As of April 2022, I have 2136 notes, and 500 [[atomic notes]]. This means that it's no longer feasable for me to manually look for connections between all of them whenever I create a new one. More and more missed links begin to appear. 

One way is through attempting to [[How can we measure similarity?|detect similiarity]] through [[machine learning]]. However, similarity is not quite what I'm looking for here. Perhaps it's useful to see which notes are *somewhat* similar, but that process can only reinforce patterns that already exist within my vault, reinforcing connections that I already understand. This is an example of how [[ML can't overcome bad data]]. 

As of right now, I'm using the Graph Analysis plugin, which leverges [[Adamic Adar]] and [[jaccard index]] to detect similarity between notes. Notably, neither of these algorithms use any information from the note other than the notes that share a connection with it. 

---
#question/pkm 