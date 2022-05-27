---
origin: 2022-05-26
---
# Ridge regression retains weak predictors. 
When using [[ridge regression]], we don't drop poor-performing features. This is because of the [[loss function]]. As we minimize $C$ and increase $\lambda$, $\beta$ can never get to zero. This makes ridge regression poor for feature selection.

This is unlike [[LASSO regression]], because [[LASSO regression drops weak predictors]]. 

---
#idea/compsci/data-science 