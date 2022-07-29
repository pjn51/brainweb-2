# Metis Notes for Wednesday, March 3rd
`LINKS:` [[metis week 9]]
#meeting/career

---
## Pair: boost
Our goal here is basically to create a class that can do [[gradient boosting]] from scratch. 

## Lecture - [[deep learning]] architectures
### Overview
Deep learning is pretty much another way to refer to the use of fancy [[neural network]]s. They have many layers and have fancy network structures that can capture a lot of relationships in the [[data]]. 

Deep learning neural networks are *universal [[function]] approximators.* They can really capture any kinds of patterns or relationships, regardless of if the patterns are linear or non-linear.

Deep learning has a ton of applications. We can do machine translation, named entity recognition, image processing, image and video captioning, chatbots, text generation, and question answering. However, there's no such thing as a free lunch. These tools require a lot of power to train. 

We have to consider the bias-variance tradeoff with deep learning architectures. These are very complex models, so the name of the game is variance reduction. We can use large training sets, dimensionality reduction, and feature selection to try and do this. In neural networks, variance increases as the number of hidden units increases. We can apply [[regularization]] via dropout layers which we'll talk about later. For more on model tradeoffs, see [[bias-variance tradeoff]].

As in a simpler NN, we have to update the weights of each node. Nodes feed forward to their successors and backpropogate to update weights. Weight matrices represent transitions between nodes. The depth of these networks can save us a lot of parameters. 

Basically, we take the input, run it through the NN, and then backpropogate to update the weights. We do all the updating using [[gradient descent]]. This process seems simple enough, but there are a ton of options for the architecture.

When we choose the architecture, we have to decide on a few things. We have to decide how many layers we will use, the types of these layers, the number of neurons per layer, and the activation function for each layer. 

We have to choose an optimizer for updating the weights. The most common choice here is stochastic [[gradient descent]], but we could also use SGD with momentum, Adam, Adagrad, or RMSprop. 

We also have to choose a [[loss function]]. For regression, we usually use [[RMSE]]. We could use hinge, or binary cross entropy for classification. We could also use categorical cross entropy. 

The deep learning workflow consists of finding an architecture that meets performance goals during training, then introducing regularization in order to limit overfitting and force the network to generalize. If the model is taking too long to train, we can use GPUs to speed that up and try and use [[transfer learning]] to skip some training.

### Deep Learning Layers
First up, we have *dense layers.* These are the simplest layers we could use. They are fully connected, meaning that every node in the output layer is a linear combination of each node in the input layer. Fundamentally, that means the network is just a bunch of [[logistic regression]]s. 

*Dropout layers* perform regularization within our network. These layers randomly ignore weights during training so that the remaining nodes are forced to learn useful information. 

- Recurrent NNs
	- These networks remember previous iterations of the NN
	- This allows dynamic temporal behavior
	- We can process arbitrary input sequences one step at a time
	- Very useful for NLP tasks where prev context matters
	- How it works
		- Hidden units are dependent on the previous unit at the same time step, and the input at the time step. 
	- Drawbacks: Fixed number of inputs and outputs
- Long short-term memory networks
	- Invented in 1997 but implemented more recently due to computing costs
	- State of the art
	- Adds an explicit memory unit. This helps get around the fact that RNNs tend to forget what they've learned from long ago.
	- Augments RNNs with ==gate units==
		- Gate units control how long events will stay in memory
		- They ask if an info is worth holding on to.
		- Input gate: causes value to become stored
		- Forget gate: causes value to be forgotten
		- Output gate: causes value to feed forward and affect the NN
- Bidirectional recurrent neural networks
	- They connect RNNs in both directions
	- Output can be dependent on future and past inputs
	- Good for context around a word, for example
	- Instead of just reading from left to right, they also read from right to left when looking at text. 
	- This has twice the time complexity as a RNN. 
- Convolutional and pooling layers
	- We talked about these on [[3-2-21 metis]]
	- This makes the data more manageable for the NN, so that we can work a bit faster
	- We have seen this for image data, but it's good for NLP as well. 
- Embedding, merge layers
	- [[embedding]] turns positive integers (indexes) into dense vectors of fixed size. This is good for compressing information. 
	- Merge layers combine outputs from multiple layers allowing us to concatenate network branches.
	- These concepts work well in conjunction with one another. 

## Lecture - intro to [[transfer learning]]
- Agenda
	- What is the structure and purpose of transfer learning
	- Applications to [[NLP]]
	- Examples beyond text
- What is it?
	- We take parameters from a model that we learned doing one predictive task, and try to use those parameters in a similar but separate context. 
	- If we have a dog detection model, we might try to apply that model to a wolf detection problem and see how it does.
	- This can speed stuff up a lot and get around issues where there just isn't enough data to train a NN on a specific problem. 
	- This is *very common* for image recognition and NLP models. 

Note: I should review the notebooks at `onl_ds5/curriculum/project-05/deep-learning-sequences` for a good overview of the different kinds of deep learning architectures. 

## [[wildfire classifier]] Meeting w Brian
- Think of the project in stages
	- MVP
	- Adding on to the project
		- Creating web app
		- Interactive viz
		- More data
- Students have done wildfire prediction in the past and it takes more time than you might think
- Start with linreg, then RF, with feature enginnering
- LinReg will probably be beat by looking at forest fire as a rate. Look into poisson regression. 