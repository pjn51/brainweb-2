---
author: 3Blue1Brown
rating:
genre: STEM
format: video
---
# 3BLUE1BROWN - [[neural network|neural networks]]
`LINKS:` [video](https://www.youtube.com/watch?v=aircAruvnKk) 
`TAGS:` #video 

---
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/aircAruvnKk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Our brains know what a 4 is, wether it's rendered in 1000 pixels or 150. That's impressive, and it's hard to get a computer to be able to do the same thing. 

There are lots of variants, and some are better than others for certian tasks. However, the vanilla network has a lot of potential. It can recognize handwriting, for instance. 

### What are neurons, and how are they linked? 
A neuron is a thing that holds a number. The network starts with one neuron per pixel in the input image, and each neuron has an activation that corresponds to the brightbess of the pixel. These are all in the first layer of the network. In the last layer, there are a lot fewer neurons. Their activiation represents how much the system thinks that each image corresponds to a certain number. The layers in the middle, the "hidden layers" are where the magic happens, but we'll deal with these later. 

Activations in one layer determine activations in the next. But how does this happen? Let's stay with the handwriting recognition example. For any letter, if we light up all the neurons that correspond with a bright pixel, that will be some sort of pattern that will be dependent on what the letter is. By passing this signal through multiple layers, we can distill the pattern down until we can point to a certain letter and say that we think the original signal corresponds with that letter. 

### Why layers?
We hope that each layer is able to break down the recognition problem into smaller and smaller sub-components. Therefore, having more layers allows the problem to be broken down into smaller and smaller problems that the machine will be able to better handle. The more complex the recognition problem, the more layers we will probably need. 

### How do layers affect one another?
Each connection has a weight assigned to it. We take all the activations and compute their weighted sum to determine the activation of their corresponding neuron in the next layer. There are fewer neurons in each sucessive layer. 

This weighted sum might be any number, but we want to squish it into the range from 0 to 1 by using the **[[sigmoid]] [[function]]**. We can apply **bias** to tell the network how high this weighted sum needs to be to approach the activation. 

Every neuron is conneted to *all* neurons from the first layer! Each one has its own weight, and its own bias. That's a lot of connections, and this number adds up when you add more layers. 

Of course, we can't tweak all these knobs and dials manually. There's just too many of them. 

### Notation
Writing all the combinations of weights, biases, and neurons is a waste of time. Instead, we use [[matrices]]. 

We write the activations from one layer as a vector, and multiply it by a matrix filled with all the weights, where each row corresponds to the connection between one layer and a particular neuron in the next layer. Then we can add the biases to this expression as a vector. As a final step, we wrap the sigmoid function around the outside. 

$$
\sigma(

\begin{vmatrix}
w_{0,0}&w_{0,1}&...&w_{0,n}
\\w_{1,0}&w_{1,1}&...&w_{1,n}
\\...&...&...&...
\\w_{k,0}&w_{k,1}&...&w_{k,n}
\end{vmatrix}
			
*

\begin{vmatrix}
a_0^{(0)}\\a_1^{(0)}\\...\\a_n^{(0)}
\end{vmatrix}

+

\begin{vmatrix}
b_0\\b_1\\...\\b_n
\end{vmatrix}

)

$$

In the above equation, $w_{k,n}$ stands for the weight of the connection, $a_n^{(0)}$ stands for the activation of neuron *n* in layer (zero), and $b_n$ stands for the bias for neuron *n*.

To compress this notation, we can rewrite the equation...

$$
a^{(1)} = \sigma(Wa^{(0)}+b)
$$

This makes the relevant code a lot simpler and faster. Many libraries optimize the hell out of matrix multiplication and this is great news due to the number of calculations. 

### Neurons as functions
A neuron takes in the output of all the outputs of the previous layer, and spits out an output between zero and one. In the same way, the whole net is really just a function that takes in an input, and spits out an output. It's really complicated and has thousands of parameters, but it's still a function. 

### Training the network
[Video link.](https://www.youtube.com/watch?v=IHZwWFHWa-w)

We will be discussing [[gradient descent]] and how we can analyze neural networks. We will be continuing the example of handwriting recognition. 

There are so many values that we can adjust in a network. The way that these values change is how the network learns. First we show the network a ton of images with labels, so that the network can know what each letter looks like, and adjust the weights and biases so that it 'agrees' with the training info being given to it. If you show the network a picture of the letter *x*, and tell it that's what *x* is supposed to look like, it will make sure that when you feed it *x*, it gives the right classification.

The hope is that this learning will generalize to new sets of [[data]], data that the network has never seen before. 

We start by initializing the weights and biases randomly. The output layer will be really bad. We have to define a [[loss function]] that tells the computer that it messed up, and to try something else. To put it mathematically, we find the sum of the differences between the correct neural value in the final layer, and the value that the model produced. We consider the average cost over the whole training set, and call this the measure for how shitty the network is. The lower this sum is, the better the model did. Now, all we have to do is to treat the whole net like a function, and try to minimize this sum. 

This loss function is a layer of compexity on top of the network. The net is taking all the inputs, and giving a few inputs. The loss function takes these few outputs and gives us a single number.

After we have this cost value, we need to get the network to improve. We can imagine how this works by imagining a simple function, like $f(x)=x^2$. We can find the minimum of this using [[calculus]]. 

We could find the slope of the function at a random point, we could 'step' to the left if the slope is positive, and 'step' to the right if the slope is negative. The drawback is that we can't guarantee that the minimum point we find is the smallest possible point overall, only that it is a local minimum. 

Of course, this is an oversimplification. The network is not simply a function dependent on one variable, it has thousands and thousands. But the math still holds true. 

This process of slowly stepping the function along is called **gradient descent**.  