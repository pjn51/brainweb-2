---
aliases: [while loop, for loop]
---
# Loops

---
# Introduction
Loops allow us to repeat sections of [[Python]] code based on some kind of logic. This helps us make code a lot more efficient in many cases. 

Loops are often used in conjunction with iterables. Iterables are objects that can return each of their contents one at a time. Lists, string, tuples, ranges, and dicts are all iterables. 

```python
For lecture in metis_lectures:
			watch(lecture)
			Knowledge += lecture
```

`while` loops are also useful, and are a little different from `for` loops. `while` loops say that while a condition is true, execute a block of code. This looping will only stop when the condition becomes false. 

```python
While python_skills < capable:
	watch(lectures)
	python_skills += lecture_info
```

The most important thing to remember with `while` loops is that you have to ensure that the loop ends eventually. A loop that runs forever will cause bad things to happen to your computer. 

`break` can manually exit a loop. 