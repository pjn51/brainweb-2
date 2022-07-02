# How is Adamic Adar calculated?
[[Adamic Adar]] is an [[graph algorithms|graph algorithm]] measure of [[How can we measure similarity?|similarity]] that predicts links in a network of nodes. It was developed in 2003 by Lada Adamic and Eytan Adar. It can be defined thusly.
$$
A(x,y)=\sum_{u∈N(x)\cap N(y)} \frac{1}{\log|N(u)|}
$$
Where $N(u)$ is the set of nodes adjacent to $u$. The script under $\sum$ is saying that we're finding the sum of $u$, which is the set of adjacent nodes that are shared between $x$ and $y$. 

A value of zero indicates that the nodes are distant, while a high value indicates closeness between nodes. 

---
#question