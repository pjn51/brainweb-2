---
author: Lilian Weng
rating:
genre: STEM
format: article
---
# Attention? Attention!
`LINKS`: [Source](https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html#:~:text=In%20a%20nutshell%2C%20attention%20in,may%20have%20read%20in%20many)
`TAGS`: #wip 
`AUTHOR:` Lilian Weng

---
> [!info]
> This is a blog post by Lilian Weng describing the idea of [[attention mechanisms]] in [[deep learning]]. 

Lilian says that we should first think about how human attention works, so that we can understand what the purpose of applying it to [[deep learning]] is. She says that human visual attention allows us to focus on certain parts of an image in high resolution, while not focusing so much on the parts of the image that we don't deem as important. 

Similarly, Lilian says we can explain the relationship of words in a sentence most accurately when we know which word combinations are worth paying the most attention to. She gives the example that if we see the word "eating," we know to expect to see a food word soon. 

In deep learning, Lilian describes attention as the practice of interpreting a [[scalars and vectors|vector]] of importance weights: in order to predict one element, we estimate using the attention vector how strongly it is correlated with (or "attends to") other elements. Then, she continues, we take the sum of their values weighted by the attention vector as the approximation of the target.

## What's wrong with Seq2Seq model?
Lilian explains that the seq2seq model was born in the field of langauge modeling, and aims to transform an input sequence (words) to a new one (target), given that both seqences can be arbitrary lengths. 

She gives an example, saying that translation is a good example of having a input in one language and a target output in another. 

Outlining the seq2seq architecture, Lilian says that normally we see an *encoder-decoder* system. She says that the encoder processes the input sequences from words to a context vector (also known as sentence [[embedding]]) of a *fixed length.* Then, she informs us that the decoder takes that context vector and transforms it into the target output. 

Lilian explains that both the encoder and decoder are made from a [[recurrent neural network]]. 

Unfortunately, Lilian explains, the fact that the vector is a fixed length means that the network often forgets the beginning of a document before it has reached the end. She says that this means the system is losing some information. 

## Born for translation
Lilian begins to discuss how the attention mechanism was created to solve this problem. She say that the innovation here was to create *shortcuts* between the context vector and the entire source input, rather than have a single context vector out of the encoder's last hidden state. 

Lilian elaborates, saying that we don't need to worry about forgetting anything, since the context vector has access to the entire input sequence, and that the alignment between source and target is learned and controlled by the context vector.

Lilian says that the context vector now makes use of three pieces of information:
1. Encoder hidden states
2. Decoder hidden states
3. Alignment between source and target

> [!question]
> Q1: What does she mean by alignment here?
> 
> ---
> Q2: If the issue with seq2seq was that the context vector couldn't fit in memory, how does the attention mechanism get around this? Wouldn't you run into the same problem?

![img](https://lilianweng.github.io/lil-log/assets/images/encoder-decoder-attention.png)

> [!note]
> From this diagram, we can see that the attention mechanism is basically telling the RNN which features to care about each time the RNN is selecting an output character. 

## Definition
Now Lilian intends to explain the attention mechanism mathematically. She wants us to imagine we have a source sequence $X$ of length $n$, and we want to output a target sequence of $Y$ of length $m$:

$X = [x_1, x_2,...,x_n]$
$Y = [y_1, y_2,..., y_n]$

She goes on to say that the encoder is a bidirectional RNN with a forward hidden state of $\overrightarrow{h_i}$ and a backward one $\overleftarrow{h_i}$. She says that a simple concatenation of the two represents the encoder state. Her reasoning is that the motivation is to include both the preceding and the following words in the annotation of one target word. 

$$
h_i = [ \overrightarrow{h_i^T} ; \overleftarrow{h_i^T} ]^T
, i = 1,...,n
$$

She explains that the decoder network has hidden state 
$s_t = f(s_{t-1},y_{t-1},c_t)$ for the output word at position $t, t=1,...,m$ where the context vector $c_t$ is a sum of hidden states of the input sequence, weighted by alignment scores:

$$
c_t = \sum{a_{t,i}, h_i}
$$

Where $c_t$ is the context vector for output $y_t$. 

$$
a_{t,i} = \text{align}(y_t, x_i)
$$

This tells us how well two words $y_t$ and $x_i$ are aligned. 

Then we take the [[softmax]] of some predefined alignment score:

$$
= \frac{\text{exp}(\text{score}(s_{t-1},h_i))}{\sum{\text{exp}(\text{score}(s_{t-1},h_i))}}
$$

> [!question]
> I have no damn idea what any of these equations are saying. 

Lilian remarks that the alignment model assigns a score $a_{t,i}$ to the pair of input at position i and output at position t, $(y_t, x_i)$ based on how well they match. She says that the set of ${a_{t,i}}$ are weights defining how much of each source hidden state should be considered for each output. 

She notes that the alignment score $a$ may be parameterized by a feed-forward network with a single hidden layer. Given that [[tanh]] is used as the non-linear activation [[function]], the author explains that the score function is used in the following way:

$$
\text{score}(s_t, h_i) = v_a^T \text{tanh}(W_a[s_t;h_i])
$$

where both $v_a$ and $W_a$ are weight matrices to be learned in the alignment model. 

The author moves on, saying that the matrix of alignment scores is a nice byproduct to explicitly show correlation between source and target words for this translation task. 

![image](https://lilianweng.github.io/lil-log/assets/images/bahdanau-fig3.png)

She recommends that we examine this [tutorial](https://www.tensorflow.org/versions/master/tutorials/seq2seq) for more instructions. 

> [!note]
> I basically wrote down all the equations and explanations word-for-word since it was over my head. Hopefully I can re-read this sometime in the future and understand this a bit better.

## A family of attention mechanisms
The author describes the differences between various sorts of attention mechanisms, but this is too over my head to understand.

## Self-attention
The author describes self-attention, also known as *intra-attention,* as an attention mechanism relating "different positions of a single sequence in order to compute a representation of the same sequence." She says that this mechanism has proved to be valuable for machine reading, summarization, and image description.

Lilian says that the [long short-term memory network paper](https://arxiv.org/pdf/1601.06733.pdf) used self-attention to perform machine reading. 

## Soft vs hard attention
The author explains that *soft attention* describes an architecture where the alignment weights are learned and placed "softly" over *all* patches of the source image, while *hard attention* means that only one patch of the image is attended to at any one time. 

She says that advanatages to soft attention include smoother, more differentiable models, but this comes at the cost of being computationally expensive, especially when the source image is large. She elaborates that hard attention requires less calcualtion at the time of inference, but means that the model is non-differentiable, and requires more complex techniques like variance reduction or [[reinforcement learning]]. 

## Global vs local attention

## Neural Turing machines

## Reading and writing

## Attention mechanisms

## Pointer network

## Transformer