# Naive Bayes can measure sentiment. 
When we're performing [[sentiment analysis]], we can use [[naive bayes]] as a simple baseline [[modeling|model]]. 

Given a corpus of text, along with a target feature letting us know if a text is positive or negative, naive bayes can perform a probabilistic analysis, counting the occurences of word $x$ in positive and negative reviews. 

This method has limitations - if a word doesn't appear in the corpus, it will have a probability of zero in appearing in a positive or negative review, messing up the results. 

---
#idea/compsci/data-science/NLP 