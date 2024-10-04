---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Hessenberg Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Hessenberg Matrix


>[!important] Definition
>A matrix $A=[a_{i,j}]\in M_{n}$ is called an **upper Hessenberg matrix** or in **upper Hessenberg form** if $$a_{i,j} =0 \quad \text{ if } i > j+1$$ i.e.  $$A = \left[ \begin{array}{ccccc}a_{11} & \cdots & \cdots  &  \star \\[5pt] a_{21} & a_{22} & \cdots &  \vdots \\[5pt]   & \ddots & \ddots &   \vdots \\[5pt] 0 &    & a_{n,n-1} & a_{nn}\end{array} \right].$$
>- An *upper Hessenberg matrix* is said to be **unreduced** if *all* its *sub-diagonal entries* are nonzero. That is, $$a_{i+1,i} \neq 0, \quad i=1\,{,}\ldots{,}\,n-1$$

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Definition
>A matrix $A=[a_{i,j}]\in M_{n}$ is called a **lower Hessenberg matrix** or in **lower Hessenberg form** if $$a_{i,j} =0 \quad \text{ if } j > i+1$$ i.e.  $$A = \left[ \begin{array}{ccccc}a_{11} & a_{12} &   &  0 \\[5pt] \vdots & a_{22} & \ddots &   \\[5pt]   &  & \ddots & a_{n-1, n}  \\[5pt] \star &    & \cdots & a_{nn}\end{array} \right].$$
>- $A$ is a *lower Hessenberg matrix* if $A^{T}$ is an *upper Hessenberg matrix*.

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]


## Explanation

>[!info]
>A **reduced Hessenberg matrix** is a **triangular matrix**.

- [[Triangular Matrix and Block Triangular Matrix]]


## Properties



## Tridiagonal Matrix

>[!info]
>A **Hermitian Hessenberg matrix** is a **tridiagonal matrix**

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]




-----------
##  Recommended Notes and References

- [[Banded System of Equations]]
- [[Triangular Matrix and Block Triangular Matrix]]

- [[Matrix Computations by Golub]] pp 15, 179, 378
- [[Matrix Analysis by Horn]] pp 35
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Numerical Linear Algebra by Trefethen]]