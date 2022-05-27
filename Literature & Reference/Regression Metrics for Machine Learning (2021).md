---
author: Jason Brownlee
rating:  
genre: STEM
format: article
---
# Regression Metrics for Machine Learning
`LINKS:` [source](https://machinelearningmastery.com/regression-metrics-for-machine-learning/)
`TAGS:` #article 
`AUTHOR:` Jason Brownlee

---
The author begins by defining [[regression]] as a type of predictive [[modeling]] problem that involves predicting a numeric value. He contrasts this with [[classification]], which he says involves predicting a class label. 

## Regression predictive modeling
Brownlee describes how predictive modeling is the mathematical problem of approximating a mapping [[function]] $f$ from input varibles $X$ to output varibles $y$. He defines this as a problem of function approximation. 

He says that regression is function approximation mapping to a *continuous* $y$. 

## Evaluationg regression models
The author begins by clarifying that we *cannot* calculate [[accuracy]] for a regression model. He elaborates that this is because accuaracy discerns between either perfectly correct predictions, and all others, while in regression getting a *perfectly* correct prediction may be impossible. Instead, the author suggests that we should be more interested in how close to perfect the predictions were. 

Brownlee says that instead of accuracy, we need to look at error, because error summarizes how close predictions were to their expected values on average. 

He outlines three error metrics that are commonly used: [[MSE]], [[RMSE]], and [[MAE]]. 

## Mean squared error
Brownlee explains that MSE is an important [[loss function]] for algorithms fit or optimized using the least squares framing of a regression problem. By least squares, he means efforts to minimize the MSE between predictions and expected values. 

The author says that MSE is the mean of the squared differences between predicted and expected target values in a dataset...

$$
\text{MSE} = \frac{1}{N \cdot (\sum{y_p - y_a})^2}
$$

...where $y_p$ is the i'th predicted value in the dataset and $y_a$ is the i'th actual value. The author highlights the fact that the difference between these two values is squared, magnifying larger errors. He says that this means MSE has the effect of punishing the model more for larger errors when used as a loss function. 

Brownlee explains that the units for this metric are "squared units." He gives the example of a finanancial model, saying that if dollars are the unit, the unit for MSE would be "squared dollars." He says this can be confusing for stakeholders, so RMSE is often substitituted.

## Root mean squared error
The author notes that the RMSE is just an extension of the MSE, where we take the root of the MSE. 