---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - tridiagonal_system_of_equations
topics:
  - numerical_linear_algebra
name: Tridiagonal System of Equations
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Tridiagonal System of Equations

![[Tridiagonal Bidiagonal and Block Tridiagonal Matrix#^06ea9d]]

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]

>[!important] Definition
>A **tridiagonal system** of equations is of form $$Tx = b$$ where $$T = \left[ \begin{array}{ccccc}a_{11} & a_{12} &  &  0 \\[5pt] a_{21} & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  a_{n-1, n} \\[5pt] 0 &    & a_{n, n-1} & a_{nn}\end{array} \right].$$
>
>In other word, the *system of equations* are $$a_{i,i-1}x_{i-1} + a_{i,i}x_{i}  + a_{i,i+1}x_{i+1} = b_{i}, \quad i=2\,{,}\ldots{,}\,n-1,$$ and $$a_{1,1}x_{1} + a_{1,2}x_{2} = b_{1}$$ and $$a_{n,n-1}x_{n-1} + a_{n,n}x_{n} = b_{n}.$$


## Explanation

>[!info]
>This system of equations naturally arises as the **finite difference equations** when *discretizing the differential equations*.



-----------
##  Recommended Notes and References


- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Matrix]]
- [[Gaussian Elimination for General Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp
- [[Matrix Computations by Golub]] pp 280 - 282
- [[Matrix Analysis by Horn]]