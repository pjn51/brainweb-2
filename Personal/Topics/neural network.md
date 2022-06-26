# Neural Networks

---
## Introduction
Neural networks, or NNs, are a [[modeling]] architecture in the field of [[deep learning]]. They use multiple layers of nodes connected in various patterns in order to become "universal function approximators."

For a great video on this concept, see [[3blue1brown video on neural networks (2017)]]. 

## Variants
NNs can be either recurrent (see [[recurrent neural network]]) or feed-forward. Feed-forward NNs have nodes whose connections do *not* form a cycle, while RNNs have nodes whose connections *do* form a cycle. Feed-forward NNs are the simplest varient. 

NNs can also belong to the [[convolutional neural network]] class. These NNs are most commonly used to analyze images, and contain convolutional layers. A layer is convolutional if it *convolves* over the input. In the case of image analysis, a convolutional layer will slide a filter across the image, looking for patterns in certain groups of pixels one at a time. 

## Further reading
![[3-3-21 metis#Lecture - deep learning architectures]]