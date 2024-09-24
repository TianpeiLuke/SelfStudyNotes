---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - lu_factorization
  - gaussian_elimination
topics:
  - numerical_linear_algebra
name: LU Factorization of Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: LU Factorization of Matrix

>[!important] Definition
>Let $A\in M_{n}$. 
>
>The **LU factorization** of $A$ is given by 
>$$
>A = L\,U
>$$
>where $L \in M_{n}$ is a *lower triangular matrix* and $U \in M_{n}$ is an *upper triangular matrix*.

- [[Gaussian Elimination for Solving Linear System]]

>[!important] Lemma
>Let $A\in M_{n}$ and suppose that $$A = LU$$ is an **LU factorization**.
>
>For any block $2\times 2$ partition
>$$
>A = \left[ \begin{array}{cc}A_{11} & A_{12} \\[5pt] A_{21} & A_{22}\end{array} \right], \quad L =  \left[ \begin{array}{cc}L_{11} & 0 \\[5pt] L_{21} & L_{22}\end{array} \right], \quad U = \left[ \begin{array}{cc}U_{11} & U_{12} \\[5pt] 0 & U_{22}\end{array} \right]
>$$
>with $A_{11}, L_{11}, U_{11}\in M_{k}$, $k\le n$, we have $$A_{11} = L_{11}\,U_{11}.$$
>
>Consequently, each **leading principal submatrix** of $A$ has an **LU factorization** in which the **factors** are the *corresponding* **leading principal submatrices** of $L$ and $U$

- [[Partition of Matrix and Block Matrix]]
- [[Principal Submatrix]]

>[!info]
>This lemma implies that **LU factorization** has a **recursive structure.**



## Explanation






-----------
##  Recommended Notes and References

- [[Gaussian Elimination for Solving Linear System]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]

- [[System of Linear Equations or Linear System]]
- [[Sparse Linear System and Graph]]
- [[Matrix]]



- [[Numerical Linear Algebra by Trefethen]] pp 147 - 171 
- [[Matrix Computations by Golub]] pp 111
- [[Matrix Analysis by Horn]] pp 216 - 223