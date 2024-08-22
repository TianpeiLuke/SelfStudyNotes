---
tags:
  - concept
  - math/linear_algebra
  - optimization/theory
  - math/matrix_analysis
keywords:
  - rank_k_approximation
  - eckhart_young_theorem
topics:
  - matrix_analysis
  - optimization
name: Rank-k Approximation of Matrix and Eckhart-Young Theorem
date of note: 2024-08-21
---

## Concept Definition

>[!important]
>**Name**: Low Rank Approximation of Matrix and *Eckhart-Young Theorem*

>[!important] Definition
>Let $A \in M_{m,n}$.
>
>The goal of **low-rank approximation** is to find a matrix $B\in M_{m,n}$ with rank $$k < \text{rank}(A) := r$$ such that $$\min_{\text{rank}(B) = k}\lVert A - B \rVert_{2}$$

- [[Bounded Linear Operator and Norm of Operator]]
- [[Rank and Nullity of Linear Map]]

## The Eckhart-Young Theorem

![[Singular Value Decomposition of Linear Map#^bcbfbe]]


>[!important] Eckhart-Young Theorem
>Let $A \in M_{m,n}$ and  $\text{rank}(A) = r$. The **SVD** of $A$ is $$A = \sum_{i=1}^{r}\sigma_{i}\, u_{i}\,v_{i}^{*}.$$
>
>If $k < r$, and $$A_{k} := \sum_{i=1}^{k}\sigma_{i}\,u_{i}\,v_{i}^{*},$$ then  $A_{k}$ is the **rank-$k$ approximation** of $A$ and $$\min_{\text{rank}(B) = k}\;\lVert A - B \rVert_{2} = \lVert A - A_{k} \rVert_{2} = \sigma_{k+1}.$$ 

^65eeb8

- [[Singular Value Decomposition of Linear Map]]

>[!important]
>Note that $A_{k}$ above is also the closest rank-$k$ matrix to $A$ in **Frobenius norm.**
>$$A_{k} = \arg\min_{\text{rank}(B) = k}\;\lVert A - B \rVert_{F}.$$



## Explanation

>[!important]
>Note that this theorem says that the **smallest singular value** of $A$ is the **2-norm distance** of $A$ to the set of all *rank-deficient matrices*.
>
>$$
>\sigma_{min}(A) = \text{dist}_{\lVert  \rVert_{2} }(A, \mathcal{S}) := \min_{\text{rank}(B) < r }\;\lVert A - B \rVert_{2} 
>$$
>where $\mathcal{S} := \left\{ B: \text{rank}(B) < \min\left\{ m,n \right\} \right\}$
>
>-- [[Matrix Computations by Golub]] pp 79







-----------
##  Recommended Notes and References


- [[Singular Value Decomposition of Linear Map]]
- [[Unitary Group]]
- [[Projection Theorem of Hilbert Spaces]]


- [[Matrix Analysis by Horn]] pp 150
- [[Matrix Computations by Golub]] pp 79