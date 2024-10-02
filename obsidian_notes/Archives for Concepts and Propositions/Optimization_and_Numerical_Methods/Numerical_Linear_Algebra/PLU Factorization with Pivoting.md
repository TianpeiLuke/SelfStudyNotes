---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - plu_factorization_matrix
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: PLU Factorization
date of note: 2024-09-26
---

## Concept Definition

>[!important]
>**Name**: PLU Factorization

![[LU Factorization of Matrix#^301e76]]

>[!important] Theorem (PLU Factorization)
>Let $A\in M_{n}$.
>
>Then there *exists* a **permutation matrix** $P\in M_{n}$, a **unit lower triangular matrix** $L\in M_{n}$, and an **upper triangular matrix** $U\in M_{n}$ such that 
>$$
>A = P\,L\,U.
>$$

^0aac00

>[!info]
>The factors above need **not to be unique**. Each $P$ corresponds to a **pivoting strategy**.

### PLU Factorization via Gaussian Elimination with Partial Pivoting

- [[Gaussian Elimination with Partial Pivoting]]


### PLU Factorization via Gaussian Elimination with Complete Pivoting

- [[Gaussian Elimination with Complete Pivoting]]



## Explanation

>[!info]
>In implementation, the $PLU$ factorization is given by **Gaussian elimination with pivoting**.

- [[Gaussian Elimination for General Linear System]]
- [[Gaussian Elimination with Complete Pivoting]]

>[!important]
>The *PLU factorization* can be written as
>$$
> PA = LU
>$$
>since $P = \hat{P}^{-1}$ is also a permutation matrix if $\hat{P}$ is a permutation.

>[!info]
>**Partial pivoting** is such a universal practice that this factorization is usually known simply as an **LU factorization** of $A$.

- [[LU Factorization of Matrix]]



-----------
##  Recommended Notes and References


- [[LPU Factorization of Nonsingular Matrix]]
- [[Triangular Equivalence of Matrices]]

- [[Gaussian Elimination for General Linear System]]
- [[Gaussian Elimination with Complete Pivoting]]

- [[Permutation Matrix and Reversal Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 219
- [[Matrix Computations by Golub]] pp 129 - 131