# Latent Dirichlet Allocation


---
## Introduction
In [[NLP]], Latent Dirichlet Allocation, or LDA, is a statistical way of [[topic modeling]]. We assume that in a corpus of documents, every document consists of a distribution of topics. Every *topic* consists of a distribution of words. Therefore, if we know both these [[distributions]], we can figure out what topics are being discussed in a document if we know each word in the document. 

## Assumptions
LDA assumes that the semantic content of a document is composed of a combination of discrete topics. Certain terms can be ambiguous, or belonging to multiple topics with different probabilities of being in one or another topic. LDA also assumes that most documents will contain a relatively small number of topics, and within each topic, there are some words that are used more frequently than others. 

## Example
For example, in an article on a soccer website, the topics of an article might be 80% "game," 10% "players," and 10% "fans." If the word "stadium," appears in the "game" topic 99% of the time and in the "training tips" topic 1% of the time, then we can deduce that the article is more likely to be related to the "game" topic than the "training tips" topic if the word "stadium" appears a lot. 

## Python implementation
Note: This code can be found [here](https://towardsdatascience.com/topic-modeling-and-latent-dirichlet-allocation-in-python-9bf156893c24). We can use the `gensim` and `nltk` libraries for [[Python]] implementation. Usually, we do some form of [[NLP]] preprocessing before we apply LDA. First, let's just import the needed packages.

```python
import gensim
from gensim.utils import simple_preprocess
from gensim.parsing.preprocessing import STOPWORDS
from nltk.stem import WordNetLemmatizer, SnowballStemmer
from nltk.stem.porter import *
import numpy as np
import pandas as pd

import nltk
nltk.download('wordnet')
```

Now we can create some functions that lemmatize and stem the text.

```python
def lemmatize_stemming(text):
	return stemmer.stem(WordNetLemmatizer().lemmatize(text, pos='v'))

def preprocess(text):
	result = []
	for token in gensim.utils.simple_preprocess(text):
		if token not in gensim.parsing.preprocessing.STOPWORDS and len(token) > 3:
			result.append(lemmatize_stemming(token)) # remove stopwords, lemmatize, stem.
	return result
```

Now we can preprocess our text that we have stored in a [[pd.DataFrame]] within [[Pandas]]. Note that our dataframe is named `text_documents`, and we're preprocessing the `description` column.

```python
processed_docs = text_documents['description'].map(preprocess)
```

Before we apply LDA directly, we need to create a "bag of words" dictionary. We first want to filter out words that appear way too infrequently, like less than 15 documents, or more than half the documents. We will keep only the most common 10,000 words within this range.

```python
dictionary = gensim.corpora.Dictionary(processed_docs)

dictionary.filter_extremes(no_below=15, no_above=0.5, keep_n=10000)
```

Now we can change this into a bag of words.

```python
bow_corpus = [dictionary.doc2bow(doc) for doc in processed_docs]
```

Now, we can finally run LDA on this bag of words corpus.

```python
lda_model = gensim.models.LdaMulticore(bow_corpus, 
									   num_topics=10,
									   id2word=dictionary,
									   passes=2,
									   workers=2)
```

This will return a model, where we can see the topics by calling `lda_model.print_topics()`. 