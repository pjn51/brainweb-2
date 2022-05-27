# TF-IDF
`TAGS`: 

---
# Introduction
In [[NLP]], TF-IDF stands for term frequency-inverse document frequency. It's a method for seeing how important a word is to a document in a corpus. It applies a weight to a specific word based on how many times the word appears in a given document *relative to the amount of times it appears overall.* 

The logic is that if a word appears in nearly every document, it likely isn't as important for us to account for than a rare word is. 

# Implementation
In [[Python]], we can use the [[Scikit-Learn]] impementation, called `TfidfVectorizer()` to vectorize the text using TF-IDF. This takes the arguments `stop_words`, `ngram_range`, and `binary`.

`stop_words` works in a similar way to CountVectorizer, where it will remove unimportant words. This tool can handle ngrams, and that's what `ngram_range` is for. `binary` indicates whether the words are actually counted up, or if there presence/absence is indicated. 

In order to actually use this, we do something like this...

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(stop_words='english')
train_tfidf = tfidf.fit_transform(X_train)
test_tfidf = tfidf.transform(X_test)
```

Now, we can fit models to `train_tfidf` and see what we can see.

# Further reading
- [[2-18-21 metis#Lecture - embedding]]