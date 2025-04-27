---
tags:
  - concept
  - recommender_system/information_filter
  - collaborative_filtering
  - memory_based_CF
  - momory_based_collaborative_filtering
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

>[!important] Definition
>**Memory-Based Collaborative Filtering** is a traditional approach to recommendation systems that directly leverages the *user-item interaction* matrix by computing similarities between users or between items to make predictions. 
>- In **user-based** collaborative filtering, the model recommends items that *similar users* have liked.
>- In **item-based** collaborative filtering, it recommends *items* similar to those *the user* has already liked. 

- [[User-Item Preference and Rating for Recommendation]]

>[!info]
>Similarity is typically measured using metrics such as 
>- cosine similarity, 
>- Pearson correlation, 
>- or adjusted cosine for rating data. 

- [[Cosine Similarity and Cosine Distance]]

### User-Based Collaborative Filtering

>[!important] Definition
>Recommend items to a user **based on other users who are similar**.
> - Example: If Alice and Bob like the same movies, recommend movies that Bob liked to Alice.
    
### Item-Based Collaborative Filtering

>[!important] Definition
>Recommend items **similar to those the user already liked**.
> - Example: If many users who liked _Movie A_ also liked _Movie B_, recommend _Movie B_.


### Algorithm

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
> 4. **Recommend items** with the highest predicted scores.



## Explanation

>[!important]
>- **Pros**
>	- Memory-based methods are 
>		- *simple*, 
>		- *interpretable*, 
>		- and require *no explicit training phase*
>- **Cons**
>	- they can struggle with 
>		- **scalability**, 
>		- **sparsity**, 
>		- and **cold-start** problems in large-scale recommendation settings.

- [[Model-based Collaborative Filtering]]






-----------
##  Recommended Notes and References




- [[Recommender Systems Textbook by Aggarwal]] pp 8, 29, 72