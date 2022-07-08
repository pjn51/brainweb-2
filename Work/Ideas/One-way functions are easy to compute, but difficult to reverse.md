# One-way functions are easy to compute, but difficult to reverse.
An example of a one-way function is the Rabin function:

$$
\text{Rabin}_N(x) = x^2 \ \text{mod} \ N
$$

We perform the above transformation of $x$, where both $x$ and $N$ are prime numbers. 

For example, if we use 3 for $x$ and 7 for $N$, we can find this result:

$$
\text{Rabin}_7(3)=3^2 \ \text{mod} \ 7 = 2
$$

Simple enough, but going from the answer 2 to finding $x$ again, even when you know $N$ is very difficult. 

[[Public-key cryptography makes use of one-way functions]] because of how difficult they are to reverse. 

---
#idea/compsci/infosec 
#idea/math 