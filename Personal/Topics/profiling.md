# Profiling
`LINKS:` [[Python]]

---
We can measure how long it takes for python to execute our program. We have to import the `time` module. Before you run your function, use `start_time = time.time( )` this will use the time function from the time module to log the time that the script begins to run. After the function runs, do this again to log the ending time, and then you can calculate the elapsed time in seconds. 

We could also use the `timeit` module but it's a little weird when it comes to the syntax. 
[[Jupyter Notebook]] has the function `%time` that can see how long a specific line of code takes to execute. 

If we wanna get more in-depth, we can use `%timeit`. This function runs the single line of code 10,000 times and gives you the average time it took to run it. It also gives the [[standard deviation]]. 
