---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - symplectic_matrix
topics:
  - linear_algebra
name: Symplectic Matrix
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Symplectic Matrix

![[Self-Adjoint Linear Map#^29c1d7]]

![[Hermitian or Symmetric Matrix#^9ff922]]

![[Hermitian or Symmetric Matrix#^657918]]

- [[Hermitian or Symmetric Matrix]]
- [[Inner Product Space]]

>[!important] Definition
>A matrix $S\in \mathbb{R}^{2n\times 2n}$ is  **symplectic** if 
>$$
> S^{T}\,J\,S = J
>$$
>where 
>$$J = \left[ \begin{array}{cc}0 & I_{n} \\ -I_{n} &0\end{array} \right] $$ is the **permutation matrix**.



## Explanation

>[!info]
>For block **symplectic matrix** 
>$$
>S = \left[ \begin{array}{cc}S_{11} & S_{12}\\ S_{21} & S_{22}\end{array} \right] 
>$$
>we have 
>$$
>S_{11}^{T}\,S_{21}, \quad S_{22}^{T}\,S_{12}
>$$
>are both **symmetric**. Moreover,
>$$
>S_{11}^T\,S_{22} = I_{n} + S_{21}^{T}\,S_{12} 
>$$






-----------
##  Recommended Notes and References



- [[Linear Map]]
- [[Matrix]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 29
- [[Introduction to Smooth Manifolds by Lee]]