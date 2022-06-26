*Markov chains are a simple text prediction method.* We can use this method to allow us to generate very simple sentences that reflect some basic relationships in a corpus of text documents. 

Given a corpus of plain text documents, we must first set up a relational dictionary that contains each unique word as a key, and has each word that follows the keyword in a list:

```python
from nltk.tokenize import RegexpTokenizer
import random
from collections import defaultdict

def markov_sentence_generator(corpus, sentence_len, start=None):
	# create the relational dict
	mydict = defaultdict(list)
	tokenizer = RegexpTokenizer(r'\w+')
    
    for note in corpus:
        tok = tokenizer.tokenize(note)
        for i, word in enumerate(tok):
            try:
                nextword = tok[i+1]
                mydict[word.lower()].append(nextword.lower())
            except:
                continue
    
    # create sentences
    sentence = []
    
    if not start:
        start = random.choice(list(mydict.keys()))
    
    sentence.append(start)
    print(sentence)
    
    for i in range(sentence_len):
        next_word = random.choice(mydict[sentence[-1]])
        sentence.append(next_word)
        
    sentence[0] = sentence[0].capitalize()
    
    return ' '.join(sentence)
```

This will create sentences that are *statistically* likely to appear, but that doesn't really mean they're at all intelligible. When trained on my brainweb notes, a sentence reads...

"Biotic and global scale life is to accomplish our mood rising above other hand in order to prevent the development of dialectics are usually longer session of the value in a part of accumulating data science workflow was actually revolutionary ideas that defends and role and economic planning on the workers."

#idea/compsci/data-science/NLP

---
```dataview
LIST
FROM [[Markov chains are a simple text prediction method]] AND -outgoing([[Markov chains are a simple text prediction method]])
```