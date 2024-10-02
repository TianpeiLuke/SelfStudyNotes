---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - lpu_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: LPU Factorization
date of note: 2024-09-26
---

## Concept Definition

>[!important]
>**Name**: LPU Factorization

![[LU Factorization of Matrix#^62518f]]

>[!important] Theorem (LPU Factorization)
>Let $A\in M_{n}$.
>
>Then there *exists* a **permutation matrix** $P\in M_{n}$, a **unit lower triangular matrix** $L\in M_{n}$, and an **upper triangular matrix** $U\in M_{n}$ such that 
>$$
>A = L\,P\,U.
>$$
>
>Moreover, the factor $P$ is **uniquely determined** if $A$ is **nonsingular**.

^463de6

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[LU Factorization of Matrix]]

## Explanation

### Triangular Equivalence

>[!info]
>The above theorem states that any *square matrix* is **triangularly equivalent** to a **permutation matrix**.
>
>In fact, permutation matrix $P$ is a **canonical form** for **triangular equivalence** for *nonsingular matrices*.

- [[Triangular Equivalence of Matrices]]


## LPDU Factorization of Nonsingular Matrix


- [[LPDU Factorization of Nonsingular Matrix]]



-----------
##  Recommended Notes and References


- [[Triangular Equivalence of Matrices]]
- [[LU Factorization of Matrix]]
- [[PLU Factorization with Pivoting]]
- [[Gaussian Elimination for General Linear System]]
- [[Gaussian Elimination with Complete Pivoting]]

- [[Permutation Matrix and Reversal Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 219
- [[Matrix Computations by Golub]]