# RMSE is a basic metric of model error.
[[RMSE]], or root mean square error, is:

$$
\frac{\sum{\sqrt{(y_p-y_a)^2}}}{n}
$$
Where $y_p$ is the predicted variance in the dependent variable and $y_a$ is the actual variance. $n$ is the number of points. 

This equation tells us how wrong, on average, we got each predicted value for $y$, and can be used as a basic [[metrics|metric]] for [[modeling]], especially for a [[linear regression]]. The result will be between zero and one, with a result of 0.3 meaning that we were 30% off on average. 

If we subtract this equation from one, we get $R^2$. [[The coefficient of determination reports the proportion of predicted vs actual variance]]. 

---
#idea/math 
#idea/compsci/data-science 
```dataview
LIST
FROM [[RMSE is a basic metric of model error]] AND -outgoing([[RMSE is a basic metric of model error]])
```