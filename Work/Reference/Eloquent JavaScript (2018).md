---
rating: WIP
author: Marijn Haverbeke
genre: STEM
---
# Eloquent JavaScript (2018)
`SOURCE:` [source](https://eloquentjavascript.net/)
`TAGS:` #book #wip 

---
> [!info]
> This is a really long book about JavaScript. I don't think that taking notes here will be a priority for me. 

# Introduction
> "We think we are creating the system for our own purposes. We believe we are making it in our own image... But the computer is not really like us. It is a projection of a very slim part of ourselves: that portion devoted to logic, order, rule, and clarity."
> -Ellen Ullman, *Close to the Machine: Technophilia and its Discontents*

The author introduces us to the purpose of this book. It is to instruct computers, when the task we want the computer to do has not yet been made possible through a program. 

When we must create our own programs, the author continues, we must use a [[programming language]]. At one point, language based interfaces such as BASIC and DOS prompts were the main tools here, but now visual interfaces are more common. They're easier to use but provide less freedom. One such language, [[JavaScript]], is built into every web browser and is available on almost every device. 

## On programming
Besides explaining JS, the author tells us, this book will introduce the reader to programming in general. Programming is hard, since we're building mazes in a way, and it is easy to get lost. 

The author advises us to follow the advice of Ursula Le Guin:

> "When action grows unprofitable, gather information; when information grows unprofitable, sleep."
> -Ursula K. Le Guin, *The Left Hand of Darkness*

The author says a program is like an immaterial machine in some ways, and a computer is a physical machine that hosts programs. Computers do stupidly simple things at blinding speeds. 

The author says that the main problem of programming is keeping programs' complexity under control. We shouldn't simply rely on best practices, the idea of limiting the usuable methods to solve problems, we should allow ourselves to develop new solutions to new problems. 

## Why language matters
The author describes the program needed to add the numbers between one and ten in previous eras:

```
00110001 00000000 00000000
00110001 00000001 00000001
00110011 00000001 00000010
01010001 00001011 00000010
00100010 00000010 00001000
01000011 00000001 00000000
01000001 00000001 00000001
00010000 00000010 00000000
01100010 00000000 00000000
```

Now the author provides the same program in JS:

```js
let total = 0, count = 1;
while (count <= 10) {
	total += count;
	count += 1;
}
console.log(total);
// -> 55
```

He observes that there are obviously some benefits to this way of doing things. We can rely on the `while` construct to control the looping behavior, and we can use `console.log` operation to print out the result. 

Simplifying this program, the author provides the same functionality while using the `range` and `sum` operations:

```js
console.log(sum(range(1, 10)));
// -> 55
```

## What is JavaScript?
The author says that JS was introduced in 1995. It was a way to add programs to web pages. We should be clear that JS has almost nothing to do with [[Java]], and the name similarity is more due to marketing than good judgement. 

The author explains that the EMCAScript standard is the document that outlines what JS really is, and what JS-supported applications need to support. 

The author describes some common complaints. JS will allow you to do basically anything, and it's therefore hard to bugfix your programs since the program won't give you error messages often. However, there are advantages to this. Namely, you have a *ton* of flexibility. 

The author notes that JS is an ever-evolving language which means tha tbrowsers have to keep up. In this book, we use the 2017 version of JS. Some [[database|databases]] such as [[MongoDB]] actually use JS, and so they have to keep up too.

## Code, and what to do with it
The author explains what code is. Code is the text that programs are made of. Most chapters in this book have a ton of code, and we should read each line carefully. Sometimes, the code examples are written for a specific environment such as Node.js. This means we have to take care if we want to run them ourselves, and we should be doing that. 

## Overview of this book
This book, the author says, has three parts. The first 12 chapters deal with JS directly. The next 7 deal with web browsers and how JS works there. The final two chapters are devoted to Node.js. 

There are also project chapters, the author tells us. They describe larger projects to give us a taste of what programming actually looks like. 

## Typographic conventions
The author says that text written in a `monospaced` font is code. Programs are written like so:

```js
function factorial(n) {
	if (n == 0) {
		return 1;
	} else {
		return factorial(n-1) * n*
	}
}
```

Sometimes, the author adds, we will write the result of a program as so:

```js
console.log(factorial(8));
// -> 40320
```

# Values, types, and operators
> "Below the surface of the machine, the program moves. Without effort, it expands and contracts. In great harmony, electrons scatter and regroup. The forms on the monitor are but ripples on the water. The essence stays invisibly below."
> -Master Yuan-Ma, *The Book of Programming*