---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - tridiagonal_matrix
  - block_tridiagonal_matrix
  - bidiagonal_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Tridiagonal Matrix and Block Tridiagonal Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Tridiagonal Matrix and Block Tridiagonal Matrix

### Square Matrix

>[!important] Definition
>A matrix $A=[a_{i,j}]\in M_{n}$ is called an **tridiagonal matrix** if $$a_{i,j} =0 \quad \text{ if } |i - j| > 1,$$ i.e.  $$A = \left[ \begin{array}{ccccc}a_{11} & a_{12} &  &  0 \\[5pt] a_{21} & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  a_{n-1, n} \\[5pt] 0 &    & a_{n, n-1} & a_{nn}\end{array} \right].$$

^06ea9d

- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Matrix Transformation]]

>[!important] Definition
>A **Jacobi matrix** is a *real symmetric tridiagonal matrix* with *positive subdiagonal entries*.

- [[Hermitian or Symmetric Matrix]]

>[!important] Definition
>A matrix $A=[a_{i,j}]\in M_{n}$ is called an **upper bidiagonal matrix** if $$a_{i,j} =0 \quad \text{ if } |i - j| > 1, \text{ or } j<i$$ i.e.  $$A = \left[ \begin{array}{ccccc}a_{11} & a_{12} &  &  0 \\[5pt] 0 & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  a_{n-1, n} \\[5pt] 0 &    & 0 & a_{nn}\end{array} \right].$$

- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Definition
>A matrix $A=[a_{i,j}]\in M_{n}$ is called an **lower bidiagonal matrix** if $$a_{i,j} =0 \quad \text{ if } |i - j| > 1, \text{ or } j>i$$ i.e.  $$A = \left[ \begin{array}{ccccc}a_{11} & 0 &  &  0 \\[5pt] a_{21} & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  0 \\[5pt] 0 &    & a_{n,n-1} & a_{nn}\end{array} \right].$$

- [[Triangular Matrix and Block Triangular Matrix]]


### Block Tridiagonal Matrix

>[!important] Definition
>A matrix $U=[A_{i,j}]\in M_{n}$  is called an **block tridiagonal matrix** if $A_{i,j} =0$ whenever $j \neq i$, where $$A_{i,j}\in M_{n_{i}}, \quad \sum_{i=1}^{k}n_{i} = n$$ i.e. $$A = \left[ \begin{array}{ccccc}A_{11} & A_{12} &  &  0 \\[5pt] A_{21} & A_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  A_{n-1, n} \\[5pt] 0 &    & A_{n, n-1} & A_{nn}\end{array} \right].$$ 
>
>

- [[Direct Sum of Subspaces]]


## Explanation
\
>[!important]
>A **tridiagonal matrix** is both an **upper Hessenberg matrix** and a **lower Hessenberg matrix**.
>
>That is a **tridiagonal matrix** is a **Hermitian Hessenberg matrix.**

- [[Hessenberg Matrix]]
- [[Hessenberg Decomposition of Matrix]]
- [[Tridiagonal Decomposition of Symmetric Matrix]]

## Properties




- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Algorithm RAM Model and Running-Time Complexity Analysis]]


## QR Factorization

>[!important] Proposition
>Let $T\in \mathbb{R}^{n\times n}$ be a **symmetric** and **tridiagonal matrix**.
>
>Then the **QR factorization** of $T$ **preserves the tridiagonal form**. That is, $$T = QR$$ where 
>- $Q\in \mathcal{O}(n)$ with **lower bandwidth** $1$
>- $R\in \mathbb{R}^{n\times n}$ is a **banded upper triangular matrix** with **upper bandwdith** $2$
>
>Moreover, $$T_{+} = RQ = Q^{T}QRQ = Q^{T}TQ$$ is also **symmetric** and **tridiagonal**.

- [[QR Factorization of Matrix]]


## Diagonalization

- [[Diagonalizable Matrix]]
- [[Simultaneously Diagonalizable Matrices]]
- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]




-----------
##  Recommended Notes and References

- [[Hessenberg Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]

- [[Matrix Computations by Golub]] pp 
- [[Matrix Analysis by Horn]] pp 35 - 36
- [[Matrix Analysis for Scientists and Engineers by Laub]]