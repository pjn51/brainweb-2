# CART Models
`LINKS:` [[modeling]]

---
CART stands for Classification And Regression Trees. These are models that use trees to predict a target based on features. 

They operate via a system of simple logical gates. Say you're trying to predict if a storm is coming. All you know is how many clouds are in the sky, the humidity, and the wind speed. A CART model might proceed in this direction: it would first take all your observations, and split them based on wether the sky was more than 50% cloudy. Then with the observations that had cloudy sky, split them based on the humidity, and so on. You see where I'm going with this. 

Here's an example of a CART model predicting if a passenger on the Titanic would survive or not. 
 
 ![titanic](https://1.bp.blogspot.com/-z7ukEqUcfvc/UPNMA9PZRKI/AAAAAAAAA2c/FitWl1yEEC0/s1600/titanic.PNG)
 
 These can be used for as [[classification]] for obvious reasons. But we can also use CARTs for [[regression]]. 