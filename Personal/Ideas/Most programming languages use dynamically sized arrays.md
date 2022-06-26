*Most programming languages use dynamically sized arrays.* They tend to avoid [[linked list|linked lists]] due to the linear complexity of indexing, and instead create [[array|arrays]] to hold data. When the size limit of an array is reached, the program will create a new array with double the size. 

Because this happens so infrequently, we can say that the average cost of appending to a list to have constant [[complexity]]. 

---
#idea/compsci 