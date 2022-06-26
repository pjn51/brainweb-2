# MNIST Classification Project
`START DATE:` [[2021-07-27]] 

---
# Introduction
I need to do a simple [[machine learning]] project to get myself back in the groove of what they're like. I guess I can just classify the MNIST handwriting dataset, which is a classic [[deep learning]] [[classification]] task. 

# Timeline
## 7-27
Ok, let's get started. First I need to get the [[data]] and make sure that the frameworks that I need will actually work on my machine, which may not be a straightforward task. I can look on Kaggle for the data. 

Ok, found the data [here](https://www.kaggle.com/hojjatk/mnist-dataset). And I've gotten it read into ny notebook successfully. Now I need to get the packages to load. 

Each element in `x_train` is a list. Within each list, there are lots of arrays, with each array representing a horizontal slice of a single number. Each of these arrays is filled with numbers that represent brightness of the pixel at that location. 

Maybe I should use NumPy to reformat the data into 2d arrays that each represent a whole number. 