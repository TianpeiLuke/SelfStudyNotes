---
tags:
  - concept
  - math/convex_analysis
  - optimization/algorithm
  - online_learning/algorithms
  - online_learning/theory
keywords:
  - follow_the_leader
  - follow_the_best_expert
  - online_learning
topics:
  - online_learning
  - online_convex_optimization
name: Follow-the-Leader Algorithm
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Follow-The-Leader Algorithm

### Follow-The-Leader in Online Convex Optimization

![[Online Convex Optimization#^93e327]]

>[!important] Definition
>Let $\mathcal{D}$ be a *convex set* and $f_{t}: \mathcal{D} \to \mathbb{R}$ be a *convex objective function* for each $t$.
>
>The **Follow-The-Leader (FTL)** algorithm find a solution that minimizes the *cumulative objective function* in the *past*. That is,
>$$
> w_{t} \in \arg\min_{w\in \mathcal{D}}\sum_{i=1}^{t-1}f_{i}(w), \quad t=1\,{,}\ldots{,}\,
>$$

^c40c08

- [[Online Convex Optimization]]
- [[Incremental Algorithm]]

### Follow-The-Best-Expert for Prediction with Expert Advice

![[Prediction with Expert Advice#^980822]]


>[!important] Definition
>Let $\mathcal{E}$ be a set of experts. 
>
>The **Follow-The-Best-Expert** algorithm makes predictions at *each time* $t$ based on the the predicts from the *expert* that **minimize the cumulative loss** in the *past*. That is,
>$$
> p_{t} = f_{E}^{(t)}, \quad \text{where } E = \arg\min_{E\in \mathcal{E}}\sum_{s=1}^{t-1}\ell(f_{E}^{(s)}, y_{s})
>$$

- [[Prediction with Expert Advice]]

## Explanation

>[!quote]
>The most natural learning rule is to use (at any online round) any vector which has **minimal loss** on **all past rounds**. This is in the same spirit of the **Consistent algorithm**.
>
>-- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 124

- [[Simple Online Learning Algorithms under Realizability Assumption]]

>[!info]
>**Follow-The-Leader** algorithm is an *incremental algorithm*. 

- [[Incremental Algorithm]]




-----------
##  Recommended Notes and References

- [[Follow-The-Regularized-Leader Algorithm]]

- [[Prediction with Expert Advice]]
- [[Exp-Concave Function]]

- [[Online Learnability and Realizabililty Assumption]]
- [[Online Convex Optimization]]
- [[Incremental Algorithm]]



- [[Prediction Learning and Games by Cesa-Bianchi]]
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 124
- [[Introduction to Online Convex Optimization by Hazan]] pp 73
- [[Foundations of Machine Learning by Mohri]]