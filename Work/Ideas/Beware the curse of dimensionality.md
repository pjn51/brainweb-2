# Beware the curse of dimensionality.
Having more features is not always going to give a more useful [[modeling]] result. In fact, it can make your model more likely to overfit. The "curse of dimensionality" describes the tendency for important differences between data points to be lost as the number of features increases. 

It helps to visualize [[data]] graphically here ([[Data can be visualized graphically]]). When we add more and more dimensions, the distance between observations increases (their similarity decreases). As the distance between *all* observations increases, the differences in distance become smaller and smaller relative to the average distance.

If a plate is 6 inches from me while another is 12, the cup is twice as far. If the same situation repeats but the plate is 5 million mines away while the cup is 5 million miles and twelve inches, you can see how that's not really a noticeable difference anymore.

This is a central reason why [[dimension reduction]] is a useful tool. 

---
#idea/compsci/data-science 