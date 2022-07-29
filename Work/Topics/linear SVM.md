# Linear SVM
`LINKS:` [tds reference](https://towardsdatascience.com/https-medium-com-pupalerushikesh-svm-f4b42800e989#:~:text=SVM%20or%20Support%20Vector%20Machine,separates%20the%20data%20into%20classes.)


---
SVM stands for support vector machine. Linear SVM is a linear [[modeling]] technique for [[classification]] or [[regression]] problems. The idea is that the algorithm creates a line or hyperplane in the feature space that separates the observations into classes. 

## Linear SVM in two dimensions
When there are only two features to work with, it's quite intuitive how linear SVM works. 

![image](https://miro.medium.com/max/1280/1*VDATmWG1E1ZNg7hdasOh5g.png)

If we have the above classification problem, we want to find the line that best separates the red and blue classes. SInce there are lots of possible lines that separate the observations perfectly, we must use *support vectors* to find the absolute best line. 

A support vector is created from the observations that are closest to the candidate line. We compute the distance between those close obseravtions and the candidate line, and that is our support vector. Our goal is to maximize the margin between the nearby observations and the candidate line. 

## Dealing with nonlinear relationships
![image](https://miro.medium.com/max/1280/1*YY8BOq-WPjRp4QkO1Xoulw.png)

If we have this situation, no line can be fitted to separate these groups. But we can add a new dimension to the data to make them linearly seperable. If we add the dimension *z* to the data, such that $z = x^2+y^2$, we can see a way to separate them in this new dimension.

![image](https://miro.medium.com/max/1280/1*a_TQSZ_H1UOA3BV299qtJQ.png)

Now that we can fit a line, *k* such that we separate the two groups, we can project this line down into two dimensions by transforming it. 

## Linear SVM in n-dimensions
We have to define the *hyperplane* in order to conceptualize this. A hyperplane in a n-dimensional Eucludian space is a flat, n-1 dimensional subset of the space that divides the space into two parts. 

## Implentation in [[Python]]
First, lets create some data to work with.

```python
import numpy as np
x = np.array([-1,-1], [-2,-1], [1,1], [2,1])
y = np.array([1,1,2,2])
```

Now that we have some data to play with, we can import and train our linear SVM from [[Scikit-Learn]].

```python
from sklearn.svm import SVC
clf = SVC(kernel = 'linear')
clf.fit(x,y)
```

To predict the class of a new observation, we would pass `prediction = clf.predict([0,6])`

## Tuning the model
The first hyperparameter we can tune is *C.* This determines the trade off between a smooth decision boundary and a correct classification. This ties into the [[bias-variance tradeoff]]. 

The second hyperparameter is *gamma.* Gamma determines how far the influence of a single training example reaches. For a low gamma, every point has a far reach, and for a high gamma, every point has short reach. When points have a higher reach, their presence influences the location of the decision boundary, while points with shorter reach are less likely to affect the location of the boundary. 