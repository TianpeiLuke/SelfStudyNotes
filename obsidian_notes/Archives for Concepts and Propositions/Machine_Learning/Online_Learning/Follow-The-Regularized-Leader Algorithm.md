---
tags:
  - concept
  - math/convex_analysis
  - optimization/algorithm
  - online_learning/algorithms
  - online_learning/theory
keywords:
  - follow_the_regularized_leader
  - online_learning
topics:
  - online_learning
  - online_convex_optimization
name: Follow-the-Regularized-Leader Algorithm
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Follow-the-Regularized-Leader Algorithm

![[Follow-The-Leader Algorithm#^c40c08]]

>[!important] Definition
>Let $\mathcal{D}$ be a *convex set* and $f_{t}: \mathcal{D} \to \mathbb{R}$ be a *convex objective function* for each $t$. Define a **regularization function** $R: \mathcal{D}\to \mathbb{R}_{+}$.
>
>The **Follow-The-Regularized-Leader (FoReL)** algorithm find a solution that minimizes the *cumulative objective function* in the *past* with an *additive regularization term*. That is,
>$$
> w_{t} \in \arg\min_{w\in \mathcal{D}}\sum_{i=1}^{t-1}f_{i}(w) + R(w), \quad t=1\,{,}\ldots{,}\,
>$$

- [[Mirror Descent Algorithm]]
- [[Online Mirror Descent Algorithm]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Follow-The-Leader Algorithm]]


## Explanation

>[!quote]
>Follow-the-Regularized-Leader is a natural modification of the basic FTL algorithm in which we minimize the loss on all past rounds plus a regularization term. The goal of the regularization term is to **stabilize the solution**.
>
>-- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 127





-----------
##  Recommended Notes and References


- [[Online Mirror Descent Algorithm]]
- [[Mirror Descent Algorithm]]
- [[Generalized Proximal Method]]
- [[Proximal Algorithm]]


- [[Follow-The-Leader Algorithm]]
- [[Prediction with Expert Advice]]
- [[Exp-Concave Function]]



- [[Online Learnability and Realizabililty Assumption]]
- [[Online Convex Optimization]]
- [[Incremental Algorithm]]




- [[Prediction Learning and Games by Cesa-Bianchi]]
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 124
- [[Introduction to Online Convex Optimization by Hazan]] pp 73 - 89
- [[Foundations of Machine Learning by Mohri]]