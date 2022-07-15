---
origin: 2022-07-13
aliases: []
---
# IQL - b2i session six
---
> [!info]
> This is the sixth session of [[IQL - From Beginner to Intermediate]].

In this lesson, we learned about subquerying. In [[IQL]], subqueries are really important, since [[IQL doesn't use joins]] at all. 

When creating a subquery, we choose the index that has the final `GROUP BY` that we want to see, and use that as our main index. The other index is going into the subquery, where we will `GROUP BY` whatever common field we're using to associate the indices.

---
1. [Slides](https://docs.google.com/presentation/d/1VXIFFKNmiZFkzbR_X4UPQeneQeeazPy6oSTaNHsBdg8/edit#slide=id.gfb64671b58_8_0)
2. [Worksheet](https://docs.google.com/document/d/1QbP4A4yuJv3gLm7A-FilTJfdP0ADSWo8RzySDitO-KA/edit#heading=h.8k60sbqz37nq)