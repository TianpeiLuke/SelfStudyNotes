---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/stochastic_process
keywords:
  - stochastic_matrix
  - doubly_stochastic_matrix
  - space_stochastic_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - stochastic_process
name: Space of Stochastic Matrices
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Space of Stochastic Matrices

![[Stochastic Matrix and Doubly Stochastic Matrix#^a60df1]]

- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Nonnegative and Positive Matrix]]

>[!important] Proposition
>Let $S$ be the space of all stochastic matrices in $M_{n}$, i.e. $$S:= \left\{ A\in M_{n}: Ae = e \right\} $$
>
>Then 
>- $S$ is a **compact space**.
>- $S$ is a **convex space**. That is, for any two stochastic matrices $A, B\in S$, and any $\alpha\in [0,1]$, we have $$\alpha A + (1- \alpha)\,B \in S $$
>- The all 1 vector $e$ is a common eigenvector for all $A\in S$.

^824e76

- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Locally Convex Space]]
- [[Compactness]]
- [[Convex Set]]
- [[Eigenvalue and Eigenvector for Linear Map]]

## Explanation





-----------
##  Recommended Notes and References


- [[Invariant Measure and Stationary Distribution]]
- [[Hidden Markov Model]]
- [[Markov Chain and Markov Process]]
- [[Nonnegative Matrix Factorization or NMF]]
- [[Markov Transition Kernel and Transition Function]]
- [[Matrix]]
- [[Positive Linear Functional]]


- [[Matrix Analysis by Horn]] pp 547 - 552
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]]