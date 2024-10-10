---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - procrustes_problem
topics:
  - matrix_analysis
name: Procrustes Problem as Approximation by Unitary Transformation
date of note: 2024-09-30
---

## Concept Definition

>[!important]
>**Name**: Procrustes Problem as Approximation by Unitary Transformation

>[!important] Definition
>Let $A, B\in M_{m,n}$. 
>
>The **Procrustes problem** refers to the problem of approximation of $A$ by the *unitary transformation* of $B$. That is, it finds an optimal $U\in \mathcal{U}_{m}$ such that
>$$
>U = \arg\min_{U\in \mathcal{U}(m)} \lVert A - U\,B \rVert_{F}^2 
>$$

^47b6c5

- [[Stiefel Manifold]]
- [[Frobenius Norm of Matrix]]

### Optimal Solution via Polar Decomposition

>[!important]
>Consider the **polar decomposition** of $AB^{*}$, $$AB^{*} = PU$$ then $$AB^{*}U^{*} = P$$ is **positive semidefinite**. It follows that
>$$
>\begin{align*}
>\lVert A - U\,B \rVert_{F}^2 &= \lVert A \rVert_{F}^2 - 2 \mathrm{Re}\left(\text{tr}(AB^{*}U^{*})\right) + \lVert B \rVert_{F}^2  \\[5pt]
>&= \lVert A \rVert_{F}^2 - 2\text{tr}(P) + \lVert B \rVert_{F}^2   \\[5pt]
>&= \lVert A \rVert_{F}^2 - 2 \sum_{i=1}^{m}\sigma_{i}(AB^{*}) + \lVert B \rVert_{F}^2 \\[5pt]
>&= \min_{U}  \lVert A - U\,B \rVert_{F}^2 
>\end{align*}
>$$


- [[Polar Decomposition of Transformation]]

## Explanation

>[!info]
>$$
>\begin{align*}
>\lVert A - U\,B \rVert_{F}^2 &= \lVert A \rVert_{F}^2 - 2 \mathrm{Re}\left(\text{tr}(AB^{*}U^{*})\right) + \lVert B \rVert_{F}^2  \\[5pt]
>&\ge \lVert A \rVert_{F}^2 - 2 \sum_{i=1}^{m}\sigma_{i}(AB^{*}) + \lVert B \rVert_{F}^2  
>\end{align*}
>$$
>with equality holds *if and only if* $$AB^{*}U^{*} \succeq 0.$$

>[!info]
>The **Procrustes problem** is used in *computer vision* and *computer graphics*.
>
>For instance, in **object matching**, it finds the *optimal rotation* on one object to **match** the other object.




-----------
##  Recommended Notes and References


- [[Invariant Subspaces Approximation for Self-Adjoint Matrix]]
- [[Procrustes Problem via Singular Value Decomposition]]
- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]
- [[Frobenius Norm of Matrix]]

- [[Singular Value Decomposition of Linear Map]]
- [[Principle Component Analysis]]


- [[Elements of Statistical Learning by Hastie]] pp 539 - 541
- [[Matrix Analysis by Horn]] pp 463
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]]