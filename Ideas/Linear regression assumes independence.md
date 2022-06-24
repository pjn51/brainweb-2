---

---
# Linear regression assumes independence. 
When performing a [[linear regression]], we're assuming that there isn't any [[covariance and correlation|correlation]] between consecutive [[residuals]]. This is important when working with time series [[data]]. 

We can evaluate this with a residual time series plot, or the Durbin-Watson test. With the former, we want to see most of the residual autocorrelation falling within the 95% confidence band. 

If this assumption is violated and correlation is positive, we can add lagged $x$ or $y$ variables. If correlation is negative, we can make sure that none of our variables are *overdifferenced.*
If correlation is seasonal, add seasonal dummy variables. 

---
#idea/math 
#idea/compsci/data-science 

1. https://www.statology.org/linear-regression-assumptions/