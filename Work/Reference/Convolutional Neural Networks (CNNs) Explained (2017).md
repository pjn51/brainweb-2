---
author: 
rating:
genre: STEM
format: video
---
# Convolutional Neural Networks (CNNs) Explained - Deeplizard
`LINKS`: [video](https://youtu.be/YRhxdVk_sIs)
`TAGS`: #video

---
<iframe width="560" height="315" src="https://www.youtube.com/embed/YRhxdVk_sIs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

A [[convolutional neural network]] is an artificial [[neural network]] that has *convolutional layers.* These networks are often used for image [[classification]], but they can serve other purposes as well. 

The unique thing that makes these networks special is their convolutional layers. These layers form the basis for a CNNs ability to detect complex patterns in an image. 

Convolutional layers do the same fundamental things that other NN layers do. They recieve an input, and they transform that input somehow, and then return an output. The way that they transform the input is special though. 

In order to transform the input, convolutional layers use a *filter.* A filter is a matrix of pre-determined size that contains numbers. We initialize these filters with random numbers that change over time as the network backpropogates. Each filter is attempting to detect a certain pattern. On a super basic level, one filter may try and look for top edges of things. Another might look for corners or something.

During transformation, the convolutional layer *convolves* (slides) this filter across the image. Areas that match the pattern that the filter is looking for have a larger output than areas that don't match it. 

CNNs usually have multiple convolutional layers that pass inputs from one to the next. In this way, we can start off by looking for basic patterns like edges or lines, and scale up in complexity as we move deeper into the CNN, until we have a network that can detect complex objects like a telephone pole or a dog. 