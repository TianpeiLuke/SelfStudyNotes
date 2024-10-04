---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - triangular_system_of_equations
topics:
  - numerical_linear_algebra
name: Triangular System of Equations
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Triangular System of Equations

![[Triangular Matrix and Block Triangular Matrix#^a825eb]]

>[!important] Definition
>An **upper triangular system** of equations is of form $$Ux = b$$ where $$U = \left[ \begin{array}{ccccc}a_{11} & a_{12} & \cdots & a_{1n} \\[5pt]  & a_{22} & \cdots & a_{2n} \\[5pt]  &  & \ddots & \vdots \\[5pt] &  &  & a_{nn}\end{array} \right].$$
>
>In other word, the system of equations are $$a_{i,i}x_{i}  \,{+}\ldots{+}\, a_{i,n}x_{n} = b_{i}, \quad i=1\,{,}\ldots{,}\,n.$$

>[!important] Definition
>A **lower triangular system** of equations is of form $$Lx = b$$ where $$L = \left[ \begin{array}{ccccc}a_{11} & &  &  \\[5pt] a_{21} & a_{22} &  &  \\[5pt] \cdots & \cdots & \ddots \\[5pt] a_{n1} & a_{n2} & \cdots & a_{nn}\end{array} \right].$$ 
>
>In other word, the system of equations are $$a_{i,1}x_{1}  \,{+}\ldots{+}\, a_{i,i}x_{i} = b_{i}, \quad i=1\,{,}\ldots{,}\,n.$$

### Bidiagonal System

>[!important] Definition
>An **upper bidiagonal system** of equations is of form $$Bx = b$$ where $$B = \left[ \begin{array}{ccccc}a_{11} & a_{12} &  &  0 \\[5pt] 0 & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  a_{n-1, n} \\[5pt] 0 &    & 0 & a_{nn}\end{array} \right].$$
>
>In other word, the *system of equations* are $$a_{i,i}x_{i}  + a_{i,i+1}x_{i+1} = b_{i}, \quad i=1\,{,}\ldots{,}\,n-1,$$  and $$a_{n,n}x_{n} = b_{n}.$$

>[!important] Definition
>A **lower bidiagonal system** of equations is of form $$Bx = b$$ where $$B = \left[ \begin{array}{ccccc}a_{11} & 0 &  &  0 \\[5pt] a_{2,1} & a_{22} & \ddots &   \\[5pt]   & \ddots & \ddots &  0 \\[5pt] 0 &    & a_{n,n-1} & a_{nn}\end{array} \right].$$
>
>In other word, the *system of equations* are $$a_{i,i-1}x_{i-1}  + a_{i,i}x_{i} = b_{i}, \quad i=2\,{,}\ldots{,}\,n,$$ and $$a_{1,1}x_{1} = b_{1}$$

## Explanation

>[!info]
>The triangular system is the by-product of 
>- **LU factorization (Gaussian Elimination)** 
>- **Cholesky factorization**
>- and **QR factorization** 
>
>during the solution of linear system.
>
>All linear system problem would end up as solving a triangular system.

- [[LU Factorization of Matrix]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[QR Factorization of Matrix]]

## Solution via Forward and Back Substitution

![[Back Substitution of Upper Triangular System#^e097d9]]

- [[Back Substitution of Upper Triangular System]]

![[Forward Substitution of Lower Triangular System#^7dde49]]

- [[Forward Substitution of Lower Triangular System]]




-----------
##  Recommended Notes and References


- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]
- [[Gaussian Elimination for General Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp
- [[Matrix Computations by Golub]] pp 280 - 282
- [[Matrix CookBook by Petersen]] pp 32
- [[Matrix Analysis by Horn]]