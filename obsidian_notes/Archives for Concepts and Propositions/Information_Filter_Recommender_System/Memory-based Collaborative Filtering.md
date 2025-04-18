---
tags:
  - concept
  - recommender_system/information_filter
keywords:
  - memory_based_collaborative_filtering
  - collaborative_filtering
  - recommender_system
topics:
  - recommender_system
name: Memory-based Collaborative Filtering
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Memory-based Collaborative Filtering



## Explanation

>[!important]
>The key **assumption** is:
> 
>- “Users who liked *similar items* in the *past* will likely enjoy *similar items* in the *future*.”


- [[Ensemble Learning]]

- [[Latent Variable Models]]
- [[Nonnegative Matrix Factorization]]
- [[Singular Value Decomposition of Linear Map]]


- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]


## Memory-based Collaborative Filtering
#### A. **User-Based CF**

- Recommend items to a user **based on other users who are similar**.
- Example: If Alice and Bob like the same movies, recommend movies that Bob liked to Alice.
    
#### B. **Item-Based CF**

- Recommend items **similar to those the user already liked**.
- Example: If many users who liked _Movie A_ also liked _Movie B_, recommend _Movie B_.


## Algorithm


> [!important] Algorithm
> The **Memory-based Collaborative Filtering (CF)** is described as below
> - *Require*:  
> 	- `R`: user-item rating matrix (rows = users, columns = items)
>1. **Calculate similarity between users**
>     - Use **cosine similarity**, **Pearson correlation**, etc.
>     - Similarity between user `u` and `v`: $$\text{sim}(u, v) = \frac{R_u \cdot R_v}{\|R_u\|\|R_v\|}$$​​
> 2. **Find top-K similar users** to the target user `u`.
>     
> 3. **Aggregate ratings from those users** for items the target user hasn't rated.
>     
>     - Usually a weighted average: $$\hat{r}_{u,i} = \frac{\sum_{v \in N(u)} \text{sim}(u,v) \cdot r_{v,i}}{\sum_{v \in N(u)} |\text{sim}(u,v)|}$$​​
> 1. **Recommend items** with the highest predicted scores.




-----------
##  Recommended Notes and References




- [[Recommender Systems Textbook by Aggarwal]] pp 8, 29, 72