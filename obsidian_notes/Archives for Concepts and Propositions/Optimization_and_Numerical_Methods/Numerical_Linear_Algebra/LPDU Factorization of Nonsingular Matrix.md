---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - lpu_factorization
  - lpdu_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: LPDU Factorization and Pivoting
date of note: 2024-09-26
---

## Concept Definition

>[!important]
>**Name**: LPDU Factorization and Pivoting

![[LU Factorization of Matrix#^301e76]]

![[LPU Factorization of Nonsingular Matrix#^463de6]]

- [[LPU Factorization of Nonsingular Matrix]]

>[!important] Theorem (LPDU Factorization)
>Let $A\in M_{n}$.
>
>Then there *exists* a **unique permutation matrix** $P\in M_{n}$, a **unique nonsingular diagonal matrix** $D$, a **unit lower triangular matrix** $L\in M_{n}$ and a **unit upper triangular matrix** $U\in M_{n}$ such that 
>$$
>A = L\,P\,D\,U.
>$$
>

^f64407

## Explanation

>[!info]
>Let $$A = L\,P\,U'$$ be the **LPU factorization**.
>Choose $$D = \text{diag}\left( \text{diag}\left( U' \right) \right)$$ thus $$U' = D\,U.$$







-----------
##  Recommended Notes and References


- [[Triangular Equivalence of Matrices]]
- [[LU Factorization of Matrix]]
- [[PLU Factorization with Pivoting]]
- [[Gaussian Elimination for Solving Linear System]]
- [[Gaussian Elimination with Complete Pivoting]]

- [[Permutation Matrix and Reversal Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 219
- [[Matrix Computations by Golub]]