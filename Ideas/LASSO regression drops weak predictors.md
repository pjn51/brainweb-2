---
origin: 2022-05-26
---
# LASSO regression drops weak predictors. 
When using [[LASSO regression]], we actually remove poorly predictive features. This is because of the [[loss function]], where as we minimize $C$ and increase $\lambda$, $\beta$ eventually reaches zero. This makes LASSO regression useful for feature selection.

This is unlike [[ridge regression]]: [[Ridge regression retains weak predictors]]. 

---
#idea/compsci/data-science 