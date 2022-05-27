---
author: 
rating:
genre: STEM
format: journal publication
---
# Attention is All you Need
`LINKS`: [source](https://papers.nips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf)
`TAGS`: #wip 

---
> [!note]
> Highlighted terms are those that I don't understand, and should look up later.
# Abstract
The authors begin by saying that up to then, the dominant ==sequence transduction== models were based on complicated [[convolutional neural network]] or recurrent [[neural network]] architectures. They propose that instead, architectures based solely on [[attention mechanisms]] are possible. While the prior models did use attention mechanisms, the authors say that the convolutional or recurrent layers can be totally done away with under this new architecure, which they label as the *[[transformer]]* architecture.

# Introduction
The authors begin by describing the methods that were being used at the time for sequence [[modeling]] and ==transduction== problems. They say that the cutting edge was found in recurrent neural networks, long short-term memory (LSTM), and ==gated== recurrent neural networks. 

The authors say that ==recurrent models typically favor computation along the symbol positions of the input and output sequences==. I think this might mean that models compute one symbol at a time, and move along the sequences as the process continues. 

From this, the authors say that recurrent models generate a sequence of ==hidden states== $h_t$ as a [[function]] of the previous hidden state $h_{t-1}$ and the input for position $t$. They say that the inherently sequential nature of this precludes parallelization during training. 

Turning to the concept of attention, the authors say that these mechanisms have become a critical part of transduction models. They say that usually, these mechanisms are used in conjunction with a recurrent network. 

They propose the Transformer, a model architecture that replaces recurrence with a reliance on an attention mechanism that they say draws "==global dependencies==" between the input and output. They say that this model architecture has performed well for translation quality, and can do so faster because of an ability to parallelize the training process.

> [!question]
> Q1: What does transduction mean?
> Q2: What is a *gated* RNN?
> Q3: What do they mean by "computation along the symbol positions?"
> Q4: What are "hidden states?"
> Q5: What are global dependencies?

# 2. Background
The authors say that the goal of reducing sequental computation forms the foundation for other models, which use convolutional NNs as basic building blocks. They say that these models compute ==hidden representations== in parallel for all input and output positions. However, the authors say that the number of operations required to ==relate signals from two arbitrary input or output positions== increases as the distance between positions increases. They contrast this with the Transformer, which always has a constant number of operations, at the cost of reduced ==effective resolution due to averaging attention-weighted positions==. They attempt to counteract this with ==Multi-Head Attention==. 

Self-attention, the authors explain, is an attention mechanism that relates different positions in a sequence in order to compute a representation of that sequence. They say that this has been used successfully in lots of tasks involving reading comprehension, summarization, and other things.

The authors continue, saying that ==end-to-end memory networks== are based on a recurrent attention mechanism instead of a sequence-aligned framework. They say that these mechanisms have been shown to work well for simple questions answering and language modeling tasks. 

Contrasting the transformer, the authors say that the Transformer is the first transduction model to rely entirely on self-attention to compte representations of input and output without recurrence or convolution. 

> [!question]
> Q1: What are hidden representations?
> Q2: What do they mean when they say that they're relating signals from two arbitrary locations?
> Q3: What is effective resolution, and how does it relate to attention-weighting?
> Q4: What is multi-head attention?
> Q5: What are end-to-end memory networks?

# 3. Model architecture
The authors explain that most neural sequence transduction models have an encoder-decoder structure. They elaborate that the encoder maps an input sequence of symbol representations ($x_1, ..., x_n$) to a sequence of continuous representations $z=(z_1,...,z_n)$. Given $z$, the decoder then generates an output sequence ($y_1,...,y_m$) of symbols, one element at a time. At each step, they say that the model is auto-regressive, consuming the previously generated symbols as additional input when generating the next. 

They say that the Transformer follows this overall architecture using ==stacked self-attention and point-wise,== fully connected layers for both the encoder and decoder. 

> [!question]
> Q1: What is a stacked self-attention and point-wise layer?

## 3.1 Encoder and decoder stacks
The authors focus first on the encoder stack, saying that the encoder stack is composed of 6 identical layers. They say that each layer has 2 sub-layers, the first of which is a multi-head self-attention mechanism, and the second of which is a "simple, position-wise fully connected feed-forward network."