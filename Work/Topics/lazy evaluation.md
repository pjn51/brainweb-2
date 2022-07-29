# Lazy Evaluation


---
## Introduction
Lazy evaluation, aka call-by-need, is an evaluation strategy for executing code that some tools use. Instead of executing the code from top to bottom, lazy evaluation means we look at the whole script, and try and run it in the most time and memory efficient way possible. This is very useful when performing [[data wrangling]] on big data. 

The opposite of lazy evaluation is eager evaluation, or strict evaluation. [[Jupyter Notebook]] defaults to eager evaluation. 

## Frameworks 
[[Dask]] and [[Spark]] (as well as [[PySpark]]) use lazy evaluation.

## Further reading
- [[3-5-21 metis]]
- [[3-8-21 metis]]