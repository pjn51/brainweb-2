# Complexity
`TAGS:`

---
# Introduction
An algorithm's complexity is a measure of the resources it uses. This includes the memory (space compexity) and the time it takes (time complexity). 

# Big-O notation [^1]
This is a way to classify the worst-case speed of an algo by looking at the order of magnitude of the execution time. [[Big O notation relates input size to run time]]. 

This is a relative representation of complexity for an algorithm.
- relative: we can only compare algorithms that perform similar tasks.
- representation: it simplifies the complexity to a single variable.

For example, what is the complexity for addition? Well, if we have two numbers of one digit each, we have to perform one operation. If we have two digits each, we have to perform two operations (adding the tens place, and then adding the singles place.) If we have to carry, we might have an additional operation. When adding two 6-digit numbers, we perform six additions (six operations). This means that we can represent the complexity as $O(n)$, or linear complexity.

Not all complexity is linear. For multiplication, we align the two numbers on top of one another, then take the first digit in the bottom # and multiply it by each digit in the top, repeating this process for all numbers, then adding the columns. This means the complexity is more like $O(n^2+2n)$. However, we really only care about the most significant term of the compexity. As $n$ increases, $2n$ recedes into meaninglessness when compared to $n^2$. So, we represent the compexity of multiplication as $O(n^2)$

[^1]: https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation

# The telephone book problem
Let's say you want to find a name in a telephone book that has 1,000,000 names. If you can't cheat by predicting where the J section starts, you could open it halfway. Upon opening it, you could see if the name you want is before or after the place you opened it. Then, you could open to halfway through the section that you now know the target name to be in. By repeating this process, you can locate the name. This is called [[binary search]]. 

Binary search has complexity $O(\log(n))$. 

# Cases for Big O
Big O can be used to determine three cases for an algo:
- best case: the ideal situation. For the telephone problem, you cound theoretically open right to the target name, making best case complexity = $O(1)$ or **constant complexity**.
- expected case: the usual situation
- worst case: the worst possible situation for the algo. 

Sometimes we are more interested in the worst case, and sometimes we're after the expected case. The best case usually isn't useful. 
# The traveling salesman problem
This is a famous problem. Given *N* towns that are linked together by 1 or more other towns by a road of a certain distance. We have to find the shortest path that visits each town. This is really hard. 

If we have three towns, here are the possible routes. 
- A → B → C
- A → C → B
- B → C → A
- B → A → C
- C → A → B
- C → B → A

For three towns, there are 6 routes. For 5, there are 60 routes. For 6 towns, we have 360 possible routes. For *n* towns, there are *n!* possible routes. This is a factoral. 

$$
5! = 5 *4*3*2*1
$$

This means that our traveling salesman problem has complexity $O(n!)$. If we had 200 towns, there isn't enough time left in the universe to solve the problem. 

# Complexity of Classification Models
See my [[1-29-21 metis]] notes. 