---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - triangular_matrix
  - block_triangular_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Triangular Matrix and Block Triangular Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Triangular Matrix and Block Triangular Matrix

### Square Matrix

>[!important] Definition
>A matrix $U=[a_{i,j}]\in M_{n}$ is called an **upper triangular matrix** if $a_{i,j} =0$ whenever $j < i$, i.e.  $$U = \left[ \begin{array}{ccccc}a_{11} & a_{12} & \cdots & a_{1n} \\[5pt]  & a_{22} & \cdots & a_{2n} \\[5pt]  &  & \ddots & \vdots \\[5pt] &  &  & a_{nn}\end{array} \right].$$
>
>If $a_{i,j}=0$ whenever $j \le i$, then $U$ is called a **strictly upper triangular matrix**.

^a825eb

>[!important] Definition
>A matrix $L=[a_{i,j}]\in M_{n}$ is called an **lower triangular matrix** if $a_{i,j} =0$ whenever $j > i$, i.e.  $$L = \left[ \begin{array}{ccccc}a_{11} & &  &  \\[5pt] a_{21} & a_{22} &  &  \\[5pt] \cdots & \cdots & \ddots \\[5pt] a_{n1} & a_{n2} & \cdots & a_{nn}\end{array} \right].$$ 
>If $a_{i,j}=0$ whenever $j \ge i$, then $L$ is called a **strictly lower triangular matrix**.

^acb7b1

>[!important] Definition
>A matrix is a **triangular matrix** if it is either a *lower triangular matrix* or an *upper triangular matrix*. 
>
>A matrix is a **strictly triangular matrix** if it is either a *strictly lower triangular matrix* or a *strictly upper triangular matrix*. 


>[!important] Definition
>An **unit triangular matrix** is a triangular matrix whose diagonal entries are all $1$s.
>

### Non-Square Matrix

>[!important] Definition
>A matrix $T\in M_{m,n}$ is **upper triangular** if 
>$$
>T = \left\{\begin{array}{cc}\left[ U, \; T_{2} \right] & \text{ if }m \le n \\[5pt] \left[\begin{array}{c} U\\[5pt] 0  \end{array}\right]  & \text{ if }m \ge n \end{array}\right.
>$$
>where $U\in M_{min\left\{ m,n \right\}}$ is *upper triangular* and $T_{2}$  is arbitrary.

>[!important] Definition
>A matrix $T\in M_{m,n}$ is **lower triangular** if 
>$$
>T = \left\{\begin{array}{cc}\left[ L, \; 0 \right] & \text{ if }m \le n \\[5pt] \left[\begin{array}{c} L\\[5pt] T_{2}  \end{array}\right]  & \text{ if }m \ge n \end{array}\right.
>$$
>where $L\in M_{min\left\{ m,n \right\}}$ is *lower triangular* and $T_{2}$  is arbitrary.

### Block Triangular Matrix

>[!important] Definition
>A matrix $U=[A_{i,j}]\in M_{n}$  is called an **block upper triangular matrix** if $A_{i,j} =0$ whenever $j < i$, where $$A_{i,j}\in M_{n_{i}}, \quad \sum_{i=1}^{k}n_{i} = n$$ i.e. $$U = \left[ \begin{array}{ccccc}A_{11} & A_{12} & \cdots & A_{1k} \\[5pt]  & A_{22} & \cdots & A_{2k} \\[5pt]  &  & \ddots & \vdots \\[5pt] &  &  & A_{kk}\end{array} \right].$$ 
>
>If $A_{i,j}=0$ whenever $j \le i$, then $U$ is called a **strictly block upper triangular matrix**.

^55b84f

>[!important] Definition
>A matrix $L=[A_{i,j}]\in M_{n}$ is called an **block lower triangular matrix** if $A_{i,j} =0$ whenever $j > i$, i.e.  $$L = \left[ \begin{array}{ccccc}A_{11} & &  &  \\[5pt] A_{21} & A_{22} &  &  \\[5pt] \cdots & \cdots & \ddots \\[5pt] A_{k1} & A_{k2} & \cdots & A_{kk}\end{array} \right].$$ 
>If $A_{i,j}=0$ whenever $j \ge i$, then $L$ is called a **strictly block lower triangular matrix**.

^96a2e3

>[!important] Definition
>A matrix is a **block triangular matrix** if it is either a *block lower triangular matrix* or an *block upper triangular matrix*. 
>
>A matrix is a **strictly block triangular matrix** if it is either a *strictly block lower triangular matrix* or a *strictly block upper triangular matrix*. 

### Qusitriangular Matrix

- [[Quasi-triangular Matrix and Quasi-diagonal Matrix]]


## Explanation

>[!info]
>A matrix is a **diagonal matrix** if it is *both* **upper triangular** and **lower triangular**.

- [[Diagonal Matrix and Block Diagonal Matrix]]

>[!info]
>The *block triangular matrix* is the representation of linear map that is **invariant within a subspace** $S$.

![[Invariance under Linear Transformation#^b37c58]]

- [[Invariance under Linear Transformation]]

## Properties



## Triangular System of Equations

- [[Triangular System of Equations]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]


## Factorization into Triangular Matrix

### General Matrix

- [[LU Factorization of Matrix]]
- [[Jordan Canonical Form]]

### Symmetric Matrix


- [[LDU Factorization of Symmetric Matrix]]
- [[LDU Factorization with Symmetric Pivoting]]

- [[Schur Triangularization and Schur Form]]
- [[Triangular Equivalence of Matrices]]

### Band Diagonal Matrix


- [[Band Triangular System of Equations]]



-----------
##  Recommended Notes and References

- [[Invariance under Linear Transformation]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Diagonal Matrix and Block Diagonal Matrix]]

- [[Matrix Computations by Golub]] pp 106 - 110 
- [[Matrix Analysis by Horn]] pp 31 - 32
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 2
- [[Numerical Linear Algebra by Trefethen]] pp 194, 218, 305- 306