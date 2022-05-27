# SpaCy
`LINKS`: [documentation](https://spacy.io/)
`TAGS`: 

---
SpaCy is a [[Python]] [[modules and packages|package]] for [[NLP]]. 

# Features
- Tokenization
- Part-of-speech tagging
- Dependency parsing (assigning labels like subject or object)
- Lemmatization
- Sentence boundary detection
- Named entity recognition
- Entity linking (disambiguating textual entities)
- Similarity
- Text classification
- Training
- Serialization

## Tokenization
[[Tokenization extracts features from text]]. First, spaCy tokenizes the text on whitespace using a method similar to `text.split()`. Then, the tokenizer processes the text from left to right, performing two checks. First, it checks if the substring matches a tokenizer exception rule. For example, "don't" is split into two substrings despite the lack of whitespace.

Then, the tokenizer checks to see if a prefix, suffix, or infix can be split from the text. 

```python
import spacy

nlp = spacy.load('en_core_web_sm')
doc = nlp("Apple is looking at buying U.K. startup for $1 billion")
for token in doc:
	print(token.text)
```

This would return...

```
Apple 
is
looking
at
buying 
U.K.
startup
for
$
1
billion
```

Let's see an example that incorporates the additional rules that we discussed.

```python
import spacy

nlp = spacy.load('en_core_web_sm')
doc = nlp("Let's go to N.Y.!")
for token in doc:
	print(token.text)
```

This would return...

```
Let
's
go
to
N.Y.
!
```

## Part-of-speech tagging and dependencies
SpaCy can parse and tag a document. This requires a trained pipeline and statistical models, which allow spaCy to predict which tag or label applies to the situation.

```python
import spacy

nlp = spacy.load("en_core_web_sm")
doc = nlp("Apple is looking at buying U.K. startup for $1 billion")

for token in doc:
    print(token.text, token.lemma_, token.pos_, token.tag_, token.dep_,
            token.shape_, token.is_alpha, token.is_stop)
```

This would return...

```
Apple Apple PROPN NNP nsubj Xxxxx True False
is be AUX VBZ aux xx True True
looking look VERB VBG ROOT xxxx True False
at at ADP IN prep xx True True
buying buy VERB VBG pcomp xxxx True False
U.K. U.K. PROPN NNP dobj X.X. False False
startup startup NOUN NN advcl xxxx True False
for for ADP IN prep xxx True True
$ $ SYM $ quantmod $ False False
1 1 NUM CD compound d False False
billion billion NUM CD pobj xxxx True False
```

