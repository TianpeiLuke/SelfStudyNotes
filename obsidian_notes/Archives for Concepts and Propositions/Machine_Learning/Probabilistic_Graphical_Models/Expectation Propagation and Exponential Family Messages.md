---
tags:
  - concept
  - machine_learning/algorithms
keywords: 
topics: 
name: 
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: 



## Explanation

>[!info]
>The idea of **expectation propagation** is to 
>- **propagate** only the **expectation** of *sufficient statistics* for each message, and 
>- use the **backward mapping** to map to the *canonical parameters* for exponential family message
>- finally, use the exponential family to *represent* the **marginal distribution** in each *clique*.

>[!info]
>Note that the $M$-projection would result in a naive **product measures** of *all CPDs* within each clique. 

>[!info]
>This method is close to **native Bayesian classification.**



-----------
##  Recommended Notes and References

- [[Information Projection and Moment Projection]]
- [[Variational Inference Formulation of Expectation Propagation]]
- [[Bethe Variational Inference for Clique Tree]]

- [[Sum-Product Expectation Propagation Algorithm]]
- [[Belief-Update Expectation Propagation Algorithm]]

- [[Maximum Entropy Learning]]
- [[Kullback-Leibler Divergence]]


- [[Exponential Family as Probabilistic Graphical Model]]
- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Probabilistic Graphical Models by Koller]] pp 442 - 445
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 107 - 124 
