# How can we select the best ML model?
Modeling is the third step in the classical [[data science workflow]] (see [[There are five fundamental data science stages]]) and is probably the most intensive step, with the most decisions to make. 

First, we need to review the question that we want to answer, and the data that we have. [[ML approaches are question-specific]] and [[ML approaches are data-specific]]. Then, we must figure out how complex the question is, because we want to use the simplest possible model to figure out the pattern at hand. [[Models must trade off between bias and variance]] and [[Complexity must be justified]]. 

For low-complexity patterns, we should probably use some sort of [[regression]]. For medium-complexity, try a [[random forest]] model. For complex patterns, we can get into [[deep learning]]. 

---
#question/data-science 
