---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords: 
topics:
  - linear_algebra
  - matrix_analysis
name: 
date of note: 2024-10-04
---

## Concept Definition

>[!important]
>**Name**: Ritz Pair for Linear Map with respect to Subspace

![[Annihilator of Subset of Vector Space#^e7f2a8]]


>[!important] Definition
>Let $\mathcal{S} \subset V$ be a *subspace* of vector space $V$ over $F$.
>
>The **Ritz pair** for linear map $A\in \mathcal{L}(V)$ *with respect to* $\mathcal{S}$ is defined as a *tuple* $(\mu, x)\in F \times V$ such that $$\left\langle  w\,,\, \left(Ax - \mu x\right)   \right\rangle = 0, \quad \forall w\in \mathcal{S}$$
>- $x\in V$ is called the **Ritz vector**
>- $\mu\in F$ is called the **Ritz value**
>- That is $$\mathcal{S} \subseteq (\{\left(A - \mu I\right)x \})^{\perp}$$

 - [[Linear Subspace]]
- [[Vector Space over a Field]]
- [[Annihilator of Subset of Vector Space]]



## Explanation





-----------
##  Recommended Notes and References


- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Annihilator of Subset of Vector Space]]

- [[Direct Sum of Subspaces]]
- [[Orthogonal Complement of Hilbert Spaces]]

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 464, 
- [[Numerical Linear Algebra by Trefethen]] pp 464, 551, 573