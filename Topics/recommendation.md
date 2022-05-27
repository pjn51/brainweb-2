# Recommendation
`LINKS:` [[modeling]]  

---
# Introduction
Recommendation is a classic [[machine learning]] task. The idea is to leverage datasets to make useful recommendations to a user. This can be done in one of two ways. The first way is called content-based filtering, and the alternative is collaborative filtering. 

# Content-based filtering
This method of recommendation uses features of the items to be recommended in order to extrapolate from a user's product rating history to provide recommendations. For example, if you liked a movie that had the attributes `[action, fast-paced, high-budget]`, then you might be recommended a movie with the attributes `[action, fast-paced, high-budget, A-list]`. 

# Collaborative filtering
This method of recommendation eskews product features, and instead uses a similarity calculation between users to provide recommendations. For instance, if Joe liked movies `[A, B, C, E]`, and Eric liked movies `[A, B, C, D, E]`, then Joe may be recommended to watch movie `C`. 

# Further reading
- [[2-19-21 metis#Lecture - recommendation]]
- [[3-10-21 metis#recommendation]]