---

---
# Linear regression assumes homoscedasticity. 
A [[linear regression]] assumes that the [[residuals]] have constant variance as $x$ increases. This property is known as *homoscedasticity*. A violation of this assumption is called *heteroscedasticity*. 

We can test this by creating a fitted value vs residual plot. This shows the [[residuals]] against the value of $x$. 

If we find heteroscedasticity, we can transform $y$, using the [[logarithms|log]] or something. We could also redefine $y$ such as choosing a rate rather than a raw number. Third, we could use weighted regression, assigning a weight to each data point based on the variance of the fitted value. 

---
#idea/math 
#idea/compsci/data-science 

1. https://www.statology.org/linear-regression-assumptions/