---
aliases: [binary search trees]
---
# Binary Search Tree
---
This is one way to organize [[data]], where each node has a left child with a smaller value, and a right child with a greater or equal value. 

```
       5
   3        8
 2   4    7   9
1        6     10
```

Finding any element in a BST has [[complexity]] equal to the height of the tree. On average, the height will be $\log(n)$, and [[Binary search trees usually have log complexity]]. 

However, if we inserted every element of a sorted [[array]] into a binary search tree, it would look like this:

```
1
 2
  3
   4
    ...
```

...and the height would be $n$. This is just a [[linked list]]! We can get around this by using a self-balancing BST that constructs itself intentionally "out of order" to avoid this issue.