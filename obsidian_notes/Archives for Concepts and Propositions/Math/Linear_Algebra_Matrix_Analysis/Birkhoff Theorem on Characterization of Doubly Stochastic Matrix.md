---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - doubly_stochastic_matrix
  - birkhoff_theorem
topics:
  - matrix_analysis
name: Birkhoff Theorem on Characterization of Doubly Stochastic Matrix
date of note: 2024-09-28
---

## Concept Definition

>[!important]
>**Name**: Birkhoff Theorem on Characterization of Doubly Stochastic Matrix

![[Stochastic Matrix and Doubly Stochastic Matrix#^a60df1]]

![[Stochastic Matrix and Doubly Stochastic Matrix#^e60317]]

![[Space of Stochastic Matrices#^824e76]]

>[!important] Birkhoff Theorem
>A matrix $A\in M_{n}$ is **doubly stochastic** *if and only if* there are **permutation matrices** $P_{1} \,{,}\ldots{,}\,P_{k}\in M_{n}$ and **positive scalars** $t_{1} \,{,}\ldots{,}\,t_{k}\in \mathbb{R}$ such that 
>- $$\sum_{i=1}^{k}t_{i} = 1.$$
>- and $$A = \sum_{i=1}^{k}t_{i}\,P_{i}$$
>  
>Moreover, $$k \le n^2 - n +1.$$  

^ad4168

- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Space of Stochastic Matrices]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Convex Hull]]
- [[Generalized Simplex]]

## Explanation

>[!important]
>The **Birkhoff theorem** shows that the *space of all doubly stochastic matrices* is a **(k-1)-dimensional simplex** where $k \le n^2-n+1$
>$$
>\begin{align*}
>S &:= \left\{ A\in M_{n}:\, Ae = e,\, e^{T}A= e^{T} \right\} \\[10pt]
>&= \text{conv}\left\{  P_{1}\,{,}\ldots{,}\,P_{n}\right\} := \left\{ \sum_{i=1}^{k}t_{i}P_{i}:  \sum_{i=1}^{k}t_{i} =1, t_{i} \ge 0 \right\} 
>\end{align*}
>$$

^f80b39

- [[Generalized Simplex]]


## Corollary

![[Convex Optimization on Space of Double Stochastic Matrices#^af83ce]]

- [[Convex Optimization on Space of Double Stochastic Matrices]]



-----------
##  Recommended Notes and References


- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Permutation Matrix and Reversal Matrix]]


- [[Matrix Analysis by Horn]] pp 549 - 550