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

>[!info]
>Tridiagonal system is a special case of **banded system**

- [[Banded System of Equations]]

## Explanation

>[!info]
>This system of equations naturally arises as the **finite difference equations** when *discretizing the differential equations*.

>[!info]
>Converting the general **symmetric system** into the **symmetric tridiagonal system** is a *critical step* in computing the **eigen-decomposition** 

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]

## Solution to Tridiagonal Equation

>[!important]
>A tridiagonal equation has **LU factorization** as it is a **banded system of equations** with upper bandwidth $q$, lower bandwidth $p$ such that  $$p =q =1$$ That is, $$T= LU$$ where $L$ and $U$ are both **bidiagonal matrix**
>
>Both *LU factorization* and the *banded forward* and *back substitution* requires **linear time complexity** $O(n)$.
>- The  *LU factorization* for solution of general linear system requires $O(n^3).$

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]
- [[Algorithm General Definition]]

![[Band Gaussian Elimination and Band LU Factorization#^bb2266]]

- [[Band Gaussian Elimination and Band LU Factorization]]

![[Band Forward Substitution and Band Back Substitution#^c7f30d]]


- [[Band Forward Substitution and Band Back Substitution]]


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