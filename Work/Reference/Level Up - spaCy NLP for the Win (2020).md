---
author: Kimberly Fessel
rating:
genre: STEM
format: article
---
# Level Up - spaCy NLP for the Win (2020)
`LINKS:` [source](https://opendatascience.com/level-up-spacy-nlp-for-the-win/)
`TAGS`: #article
`AUTHOR:` Kimberly Fessel

---
Kimberly begins by outlining the role of [[NLP]] in [[data science]]. She sasys that it's a branch of artificial intelligence in which computers extract information from written or spoken words. She explains that the open-source library [[spaCy]] is useful for processing text quickly and accurately, within a simple framework.

She notes that spaCy offers a streamlined approach which is more pragmatic than other libraries like NLTK, which she says is more geared towards research. She also explains that the 'Cy' in spaCy indicates that it incorporates some [[Cython]] principles, making it very fast. 

## Installation
To install, Kimberly outlines how we can download it using pip and the [[command line]]. She notes that we will also have to install the english language model along with the library.

```
pip install slacy
python -m spacy download en_core_web_sm
```

## Tokenization
In order to tokenize text, Kimberly says we can perform the following command in python:

```python
import spacy
nlp = spacy.load('en_core_web_sm') # load the langauge model
review = "I'm so happy I went to this awesome Vegas buffet!"
doc = nlp(review)
```

She says that this will result in a spaCy document consisting of a rich collection of tokens with many attributes including parts of speech, lemmas, dependencies, and named entitites. She says that we can loop over each token in the document and print whatever characteristics we're interested in. 

Kimberly also remarks that spaCy does this tokenization in a nondestructive way - retaining the natural structure of the text that we can rebuild using `doc.text`. 

## Dependencies
Turning to the issue of *dependencies,* Kimberly says that determining the real meaning of words is dependent on context. She gives the example of "bear," saying this could be referring to a furry animal or the struggles that one is enduring. She says that to deal with this, spaCy creates a a*dependency tree* which can be visualized via `displacy`.

In order to use `displacy`, Kimberly instructs us to...

```python
from spacy import displacy
displacy.render(doc)
```

This will result in the following image...

![tree](https://user-images.githubusercontent.com/13643239/41405459-14eee2c8-6fca-11e8-97aa-633b8948b33f.png)

...where we can see the relationships between each word in the document.

## Named entity recognition
Kimberly also says that we can perform named entity recognition using spaCy. She says that this happens automatically when spaCy runs text through the langauge model. She instructs us to cycle through `doc.ents` in order to see what entities spaCy is picking up.

She says that this will return an acronym next to each entity, and we can ask spaCy to explain what each acronym means by passing `spacy.explain(<acronym>)`. 

Kimberly also notes that we can ask spaCy to render it's understanding visually using `displacy.render(doc)`. This will result in...

![rendered](https://miro.medium.com/max/1586/1*hsCqEsqSlI2zn-r9MWRTPQ.png)

...the text, overlaid with what spaCy understands about it.

## Conclusion
Kimberly concludes that spaCy provides an intuitive framework for NLP. She mentions that there are other tools that we didn't discuss, such as detecting noun phrases, similarity scoring, character matching, and categorization built into spaCy.