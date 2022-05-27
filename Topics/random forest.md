# Random Forest 🌲🎲🌲
`TAGS:`  

---
For an introduction to Random Forest, see my [[2-1-21 metis]] notes.

Random Forest is one of the [[CART models]] that attempts to get around some issues faced by simpler decision trees. 

When decision trees try and find patterns, they sometimes seize upon one or two features that are the most explanatory. It's good that they are paying attention to those important features, but we also want to try and gather information from the features that aren't as powerful individually. 

That's where the random in Random Forest comes in. RF makes sure that the trees stay uncorrelated by randomly excluding certain features at each split in each tree. This makes sure that all the trees are using different methods to try and describe the pattern in the data. 

After all the trees come to their chosen strategy for regression or classification, RF aggregates all their results back together again. 

![[2-1-21 metis#Lecture - random forest]]