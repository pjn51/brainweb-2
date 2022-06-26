---
origin: 2022-06-09
---
# CNNs use kernels to find patterns. 
A [[convolutional neural network|CNN]] attempts to detect complex patterns based on simple building blocks. The convolutional layer in the CNN slides a *kernel* along the dataset (usually an image). 

The kernel scores areas of the image that align with the pattern the kernel is looking for, such as a corner or edge. This data is fed into the next layer, which may be looking for shapes like circles or squares, and further layers that detect more complex shapes. 

---
#idea/compsci/data-science 