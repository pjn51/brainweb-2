# Metis Notes for Tuesday, March 9th
`LINKS:` [[metis week 10]]
`TAGS:` #meeting/career

---
## Pair: affair
We're discussing a 1970s dataset of marriage features and whether or not the wife was having an affair with the husband. The purpose is to get into some of the [[data ethics]] questions around creating [[classification]] using this [[data]]. 

One question is if the data is drawn from a representative [[sample and population| sample]] of the US population. The data were gathered from write-in responses to a womens' magazine. For instance, the data excluded women who were unemployed or who had been married more than once. These kinds of decisions are normative. 

## [[deep learning]] test review
Here are all the questions I got wrong, along with the correct answers. 

>   Suppose you are planning to train a standard convolutional neural network model on a dataset of 60,000 RGB color images with 50x50 pixel dimension. Which of the following feature input array shapes would be CORRECT for training this network in keras?

The correct answer is 60,000 by 50 by 50 by 3. 

> Suppose you are planning to train a standard recurrent [[neural network]] model on a dataset of 100,000 text documents, each exactly 50 words long. You choose to represent each word in a document using a pre-trained, 300 dimensional word embedding. Which of the following feature input array shapes would be CORRECT for input into a keras recurrent layer?

The correct answer is 100,000 by 50 by 300. We have 100,000 documents, with a length per document of 50 words, and we have 300 as our size of the pre-trained vectors that each word corresponds to. The fact that it's a recurrent NN doesn't really matter. 

> Which of the following is a CORRECT description of how a single filter uses the convolution operation to process a 2-dimensional matrix input?

The correct answer is "The filter slides horizontally and vertically across the matrix, computing a localized linear combination of filter weights and matrix entries to fill each corresponding unit of output." We have our box of numbers (kernel) and we slide it across the image, computing a linear combination of the pixel values. 

> Which of the following statements about the use of pooling layers in convolutional neural networks (CNNs) is FALSE?

The correct answer is "Pooling layers directly replace activation functions, which are excluded from CNNs." Pooling layers and activation functions do different things. Pooling layers take the output of the previous layer and take the highest values from each one, giving us a larger view. Activation functions are adding the non-linear combinations to get us our output. They don't replace one another. 

> Which of the following is a CORRECT description of what a flattening layer accomplishes in a convolutional neural network?

The correct answer is "It converts a 3-dimensional tensor to a vector with the same number of total entries." If we have a n-dimensional vector, a flatterning procedure will put it into fewer than n dimensions. 

> Which of the following is a CORRECT description of how a recurrent neural network (RNN) layer processes a sequence of vectors?

The correct answer is "The RNN layer iterates vector by vector, using each input vector along with its current memory state to update its memory state until it reaches the end of the sequence." This is a time-series process where we take into account the temporal relationship between the features.

> Which of these is a CORRECT description of how a recurrent neural network (RNN) layer’s output can be mapped to a single prediction output?

The correct answer is "The RNN layer’s final memory state vector is used as flat input into fully connected layers that terminate in the final prediction." 

> You are working on developing an application that scores the overall visual quality and coherence of a series of presentation slides. You have access to a dataset of slide image sequences (i.e. PowerPoint presentations), labeled on a scale of 1 to 10 for overall aesthetic quality across all slides. Which of these deep learning approaches would BEST match the structure of this problem?

The correct answer is "Run a CNN on each slide, using the output to construct a sequence; pass this sequence to an RNN whose output is the target prediction."

> Which of the following is a CORRECT description of how transfer learning is applied in text processing recurrent neural networks (RNN)?

The correct answer is "Pre-trained word embeddings are used as vectorized representations of words, which are passed in a sequence as input to custom trained RNN layer(s)."

## Lecture - [[noSQL]]
First, we need to discuss some terminology. We refer to [[database]] management systems, such as noSQL, as DBMS (data base management systems.) When these systems are *relational*, we refer to them as RDBMS. These systems have data stored in tables. 

When working within these systems, we have basic functionality that we'll always see across systems. This is referred to as CRUD: create, read, update, and delete. We will also be thinking about the *schema.* The schema is a static model of the data in the database, and describes relationships between data. In non-relational databases, this is much more flexible. Schemas have to be planned in advance, and changing the schema is akin to changing the whole database.

Now we can move on to discuss what noSQL really is. It is an abbreviation of "not only [[SQL]]." One example of a noSQL platform is [[MongoDB]]. 

These systems store data in documents instead of rows. In MongoDB, these documents are BSON documents, meaning that they're stored in binary serial object notation.

We should use noSQL systems like MongoDB when the data is unstructured and requires flexibility, or when we find that a standard [[SQL]] database is needing to add more and more tables to represent complex relationships. MongoDB is also best for a large size of the data, like 5-10 GB per table. 

## Lecture - graph databases
Neo4j is an example of a [[graph databases|graph database]]. With relational data, we have multiple tables, and the attributes of a specific product might be spread among many tables. This relationship could be visualized as a graph structure of nodes and arrows. 

A graph [[database]] takes there relationships and puts them in a giant graph of all relationships across all tables. This naturally normalizes the data, and is really flexible when new relationships are introduced.