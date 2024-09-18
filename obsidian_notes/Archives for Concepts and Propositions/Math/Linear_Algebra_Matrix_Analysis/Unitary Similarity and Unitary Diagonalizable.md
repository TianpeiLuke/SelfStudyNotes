---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - unitary_similarity_matrix
  - orthogonal_similarity_matrix
  - unitary_diagonalizable_matrix
  - orthogonal_diagonalizable_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Unitary Similarity
date of note: 2024-09-16
---

## Concept Definition

>[!important]
>**Name**: Unitary Similarity and Unitary Diagonalizable

![[Similarity Relation between Linear Maps and Matrices#^5ebca6]]

>[!important] Definition
>Let $A, B\in M_{n}$ be $n\times n$ matrix. 
>
>We say $A$ **is unitarily similar to** $B$ if there exists a *unitary* $U\in \mathcal{U}(n) \subset M_{n}$ such that 
>$$
> A = U\,B\,U^{*}
>$$
>- If $U$ may be taken to be *real orthogonal matrix*, then $A$ is said to be **real orthogonally similar to** $B$. $$A = U\,B\,U^{T}$$

^9aed0a

- [[Similarity Relation between Linear Maps and Matrices]]


>[!important] Definition
>Let $A \in M_{n}$ be $n\times n$ matrix. 
>
>We say $A$ **is unitarily diagonalizable**  if it is *unitarily similar to* a *diagonal matrix*. That is, there exists a *unitary* $U\in \mathcal{U}(n) \subset M_{n}$ such that 
>$$
> A = U\,\Lambda\,U^{*}
>$$
>- If $U$ may be taken to be *real orthogonal matrix*, then $A$ is said to be **real orthogonally diagonalizable**. $$A = U\,\Lambda\,U^{T}.$$

^be2b64

- [[Diagonalizable Matrix]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


## Explanation


## Norm Invariance 

>[!important] Theorem
>Let $U\in \mathcal{U}(n)$ and $V\in \mathcal{U}(m)$ be **unitary**, and let $A = [a_{i,j}]\in M_{n,m}$ and $B = [b_{i,j}]\in M_{n,m}$, and suppose that $A$ is transformation of $B$ $$A = U\,B\,V.$$
>
>Then **Frobenius norm** of $A$ is **equal** to the  **Frobenius norm** of $B$ 
>$$
>\lVert A \rVert_{F}^{2} = \sum_{i,j}|a_{i,j}|^2 = \sum_{i,j}|b_{i,j}|^2 = \lVert B \rVert_{F}^2.  
>$$
>- In particular, if $m=n$, and $V= U^{*}$, i.e. $A$ is **unitarily similar to** $B$, then this identity is satisfied.

- [[Frobenius Norm of Matrix]]




## Isometry and Isometric Isomorphism

- [[Isometry and Isometric isomorphism]]



-----------
##  Recommended Notes and References


- [[Unitary Group]]

- [[Schur Triangularization and Schur Form]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Equivalence Relation]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 95 - 101
- [[Matrix Computations by Golub]]