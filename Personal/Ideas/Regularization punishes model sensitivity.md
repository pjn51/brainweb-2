*Regularization punishes model sensitivity.* [[regularization]] is any step that we take in order to avoid [[modeling|model]] overfitting, and one way to avoid overfitting is to make our model less sensitive to each data point. This is an important tool because [[Sensitive models risk hallucinating patterns]]. 

We can quantify the sensitivity of our model by taking the sum of all the coefficients present in the algorithm. We call this $\sum{\beta}$. When we square this, resulting in $\sum{\beta^2}$, we have a term that increases as the sensitivity of our model to each datapoint increases. 

If we incorporate this into our [[loss function]], along with $\lambda$, which controls the degree of regularization, we can tune our model by increasing or decreasing lambda, and increasing or decreasing the amount we want to punish our model for sensitivity. 

#idea/compsci/data-science 

---
```dataview
LIST
FROM [[Regularization punishes model sensitivity]] AND -outgoing([[Regularization punishes model sensitivity]])
```