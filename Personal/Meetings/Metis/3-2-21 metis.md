# Metis Notes For Tuesday, March 2nd
`LINKS:` [[metis week 9]]
`TAGS:` #meeting/career

---
## Pair - [[neural network]]  with Keras
For a code walkthrough, see `NN_with_keras.ipynb` in `onl_ds5/curriculum/project-05/deep-learning-convolutions`

We first have to define our inputs and outputs. Then we define the network architecture (layers, activation functions, etc). The third step is to compile the model with an optimizer, the loss [[function]], and the tracking metric. 

After that, we will fit the model and evaluate performance. 

Standard import, getting the [[data]]. We will be using a built-in dataset about housing information. 

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

from tensorflow.keras.datasets import mnist, boston_housing

from sklearn.model_selection import train_test_split

(x_train, y_train), (x_test, y_test) = boston_housing.load_data()
```

Define inputs and preprocessing. NNs need everything on the same scale. 

```python
from sklearn.preprocessing import StandardScaler

ss = StandardScaler()
x_train_scaled = ss.fit_transform(x_train)
x_test_scaled = ss.transform(x_test)
```

Now let's be more explicit about what we're really putting into the neural network. The input here is a single [[scalars and vectors|vector]]. We will use a sequential base, adding layers one by one as we construct it. Therefore, we can use the `Sequential()` method in `keras`. We use `input_shape=13` because this data has 13 features.

```python
model = keras.Sequential()

model.add(layers.InputLayer(input_shape=(13,))) #this adds a layer to the model
```

Now let's add two dense layers. This means that every node from this new layer has a connection to every node in the previous layer. When we add layers, we bring in more "automatic feature creaters" into the problem. As we add more and more layers, we will capture more and more complex patterns that might exist between the features. We use the [[sigmoid]] activation function here. 

```python
model.add(layers.Dense(10, 	# this new layer has 10 neurons
					   activation = 'sigmoid')) # and uses the sigmoid activation func

model.add(layers.Dense(5,	# this layer has 5 neurons and uses the sigmoid func
					   activation = 'sigmoid'))
```

Now let's add an output layer. Since we just want the final price of the house, we want this layer to be a single neuron. We don't give an activation function because we just want it to spit out a number. 

```python
model.add(layer.Dense(1))
```

Now that we have the model, we can see a summary of the model using `model.summary()`. 

Now we can compile the model. We will use stochastic [[gradient descent]] as our optimizer. The [[loss function]] is what determines the changes to the weights. We will use mean square error (see [[bias-variance tradeoff]]). We will also track mean absolute error just to see what it is. This won't affect the weights.

```python
model.compile(optimizer='SGD',
			  loss='mse', 
			  metrics=['mae'])
```

Now we fit the model to the training data. We have to worry about `batch_size`, which is the number of observations we consider every time we update the weights. If we consider *all* observations in between each update, that might take a while or we might not be able to fit the whole thing into memory at the same time. For us this is pointless since the dataset is small. Batch size also prevents us from overfitting. `epochs` refers to the amount of times the network sees the whole data set. We need to set a low enough parameter here to prevent overfitting, while allowing the model to see the data enough to see all the patterns. For us, 100 epochs should be good.`validation_split` let's us perform a validations step automatically every epoch. `callbacks` is used to save the output of our models to a file for later. We save this model as `history` so that we can look back on the epochs and see how the errors change as the network works. 

```python
history = model.fit(x_train_scaled, y_train,
		  			epochs=100,
		  			validation_split=0.2,
		  			callbacks=[keras.callbacks.ModelCheckpoint('models/mnist.{epoch:02d}-{val_loss:.2f}.hd5f', save_best_only=True)])
```

`history` will be a [[dictionaries|dictionary]] that shows the error metrics that we wanted to track. If we wanted to, we could plot how mean square error changes as the model looks at the data again and again.

After we see the errors, we need to go back and change the [[hyperparameters]]. We could add more layers, more nodes to each layer, change activation functions, change the optimizer, or do other things to see if we can get the NN to do a little better. 

## Lecture - [[convolutional neural network]] 
When we think about images, we have to break them down into their simplest components. Images are really just a lot of pixels with a color value for each pixel. There are a *lot* of possible combinations of color values and patterns for even a small image. However, we can extract some generalities across pictures. Pixels nearby one another tend to be similar to one another. We can also see that high level patterns ('chair') are built on low level patterns ('line'). 

We can exploit the correlation of nearby pixels using *convolution.* In order to do this, we take a magnifying glass of sorts, called *the kernel*, and slide it across the image so that we examine groups of pixels at a time. This kernel looks for low level patterns in that specific group of pixels. Each kind of kernel is looking for one specific pattern. These kernels can recognize whatever pattern they are looking for, regardless of where it is in the image, which is nice.

The many layers of a *convolutional neural network* use these kernels to find low-level patterns and build on them to detect complex patterns that are made up of many lower-level patterns. The CNN works by finding the optimal values for the kernels in order to pick up on the low level patterns that are used to build towards detecting high level patterns. For example, a kernel that could pick up on vertical lines might take this form:

$$\begin{vmatrix}0&1&0\\0&1&0\\0&1&0\end{vmatrix}$$

If a certain region of the picture aligns with this kernel, we would get a high score for that area. This is called having a *high expression.* 

CNNs often need to reduce the feature space to speed up their work. In order to do this, we can use a method known as *max pooling.* We take the maximum expression value from a group of pixels instead of all the individual values. We can do this since we care about the existence of a feature in a space, not the average expression of a feature. If a region of the picture has a high expression somewhere, we just care about that, not the average of the region in which the feature may be located. 

### Working With the MNIST Dataset
Let's try and classify handwriting using a CNN. 

We have to import a bunch of stuff, and then we get the data. This is the MNIST dataset that we've worked with in the past. We create a train-test split like we usually do, and then we convert it to categories by using `np_utils.to_categorical()`. 

```python
from sklearn.datasets import fetch_openml
import numpy as np
from sklearn.model_selection import train_test_split
from keras.utils import np_utils

'''
data setup: load data, 4D tensor formatting, train-test split,
and 2D (one-hot encoded) representation of the training target
'''

mnist = fetch_openml('mnist_784')

X_digits, Y_digits = mnist.data, mnist.target.astype(np.int64)
X_digits = X_digits.reshape((-1,28,28,1)) #28x28 images with only 1 color channel

X_train, X_test, y_train, y_test = (train_test_split(X_digits, Y_digits, 
                                                     test_size = .2, random_state = 42))

y_train_cat = np_utils.to_categorical(y_train)
```

Now we can import the models that we will use, and then we instantiate a sequential NN. We add an input layer to the net, in the shape of the training data. 

```python
import keras
from keras.models import Sequential
from keras.layers import Dense, Conv2D, MaxPooling2D, Flatten, GlobalAveragePooling2D, InputLayer
'''
 In this network structure, note that we follow the typical CNN heuristic of 
 gradually reducing width and height dimenions over time with max pooling
 (typically by a factor of 2), but increasing the filter depth dimension 
 to find increasingly specific patterns. These models are typically compromised 
 of a series of convolutional blocks followed by a flattening operation and 
 a series of fully connected layers at the terminus.
'''

NN = Sequential()

NN.add(InputLayer(input_shape=X_train.shape[1:]))
```

Now we can begin to add more layers to the model. We're using `Conv2D` which is a convolution that slides over width and height. We also use a `MaxPooling2D` layer, which pools over width and height. We alternate between a few of these, and then we add a few dense layers at the end.

```python
# Conv block 1.  You can add more conv steps to
# each block to increase model capacity.
NN.add(Conv2D(filters=10, kernel_size=3, activation='relu', padding='same'))
# NN.add(Conv2D(filters=16, kernel_size=3, activation='relu', padding='same'))
NN.add(MaxPooling2D())

# Conv block 2 - note we increase filter dimension as we move
# further into the network. You can add more conv steps to
# each block to increase model capacity.
NN.add(Conv2D(filters=20, kernel_size=3, activation='relu', padding='same'))
# NN.add(Conv2D(filters=16, kernel_size=3, activation='relu', padding='same'))
NN.add(MaxPooling2D())

# Conv block 3 - The conv blocks should be ended with either a flatten
# layer or a global pooling layer. These transform the 2D layers to 1D
# to match the following dense layers.
NN.add(Conv2D(filters=30, kernel_size=3, activation='relu', padding='same'))

NN.add(GlobalAveragePooling2D())

# Fully connected block - flattening followed by dense and output layers
# NN.add(Flatten())
NN.add(Dense(20, activation='relu'))
NN.add(Dense(10, activation='softmax'))  # 10 target classes
```

Now we just compile and fit the model, saving the output to another folder. We're using a categorical cross entropy loss function, and using [[accuracy]] as our metric. 

```python
NN.compile(
    loss='categorical_crossentropy',
    optimizer='adam',
    metrics=['accuracy'],
)
NN.summary()
NN.fit(X_train, y_train_cat, epochs=5, verbose=1, validation_split=0.25,
       callbacks=[
           keras.callbacks.ModelCheckpoint(
               'models/mnist.{epoch:02d}-{val_loss:.2f}.hdf5',
               save_best_only=True)
       ])  # track progress as we fit
```

Now we can see what kind of [[accuracy]] we're getting with the model. We will try and predict the classes of the handwriting in the test set. 

```python
from sklearn.metrics import accuracy_score
accuracy_score(y_test, NN.predict_classes(X_test))
```

### Using Pre-Trained CNNs
There are tons of pre-trained networks out there. An architecture has already been defined and data has already been applied to it. The weights have already been trained to solve a certain problem. The most common dataset is ==ImageNet== which is a bunch of images of different things. 

Common pretrained ImageNet models include
- VGG16
- VGG19
- InceptionV3
- MobileNet

This saves a massive amount of time, since these models are pretty easy to adapt to whatever problem we're working on. It's typical to take a pre-trained model and add and train from scratch the fully connected block at the end of the network. All we have to do is change the output layer, so that the model is no longer doing classification based on the 1000 classes in ImageNet. Now our model can do any sort of classification that we want. If we only want to tell if the image is fruit or not, we change it from a 1000 class classification problem to a 2 class classification problem, where one is fruit and one is not-fruit. 

We download the mobilenet dataset, and let's create a function to prepare images that we get from that dataset. The function loads an image, turns it into an array, and does some preprocessing.

```python
from keras.applications import mobilenet_v2
from keras.preprocessing import image

def prepare_image(img_path):
	img = img.load_img(img_path, target_size=(224, 224))
	x = img.img_to_array(img)
	x = np.expand_dims(x, axis=0)
	x = mobilenet_v2.preprocess_input(x)
	return x
```

Now we load an image and try and predict what's in the image. 

```python
model = mobilenet_v2.MobileNetV2(weights='imagenet')

x = prepare_image('img/dog.jpeg')

out = model.predict(x)
```

CNNs are mainly for images, but we can use them any time there's a spatial or temporal relationship to predict. 