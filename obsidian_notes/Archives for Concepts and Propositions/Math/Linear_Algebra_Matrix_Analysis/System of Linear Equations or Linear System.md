---
tags:
  - concept
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - system_of_linear_equations
  - linear_system
topics:
  - linear_algebra
  - numerical_linear_algebra
name: System of Linear Equations
date of note: 2024-09-15
---

## Concept Definition

>[!important]
>**Name**: System of Linear Equations or *Linear System*

>[!important] Definition
>Let $A = [a_{i,j}] \in M_{m,n}(F)$ be a matrix of dimension $m\times n$, and $b = [b_{i}]\in F^{m}$ where $F$ is a *field*.
>
>The **linear system** or **system of linear equations** is defined as
>$$
>\begin{align*}
> a_{1,1}x_{1} \,{+}\ldots{+}\,a_{1,n}x_{n} &= b_{1}\\[5pt]
> a_{2,1}x_{1} \,{+}\ldots{+}\,a_{2,n}x_{n} &= b_{2}\\[5pt]
> \ldots& \\[5pt]
> a_{m,1}x_{1} \,{+}\ldots{+}\,a_{m,n}x_{n} &= b_{m}\\[5pt]
>\end{align*}
>$$
>- In **matrix compact form**, the linear system can be written as
>$$
>Ax = b
>$$
>where $x\in F^{n}$.
>- The matrix $A$ is called the **coefficient matrix**,
>- If $b = 0$, the system is said to be **homogeneous**.
>- $x\in F^{n}$ is called a **solution** of *linear system* if it satisfies the above equations. In other word, $x$ are coefficients that $$b= \sum_{i=1}^{n} A_{i}\,x_{i}$$ where $A_{i}\in R(A)$ are independent columns in range of linear map.

^818e89

- [[Range and Kernel of Linear Map]]
- [[Vector Space over a Field]]
- [[Field]]

>[!important] Definition
>A **matrix linear equations** is defined as 
>$$
>AX = B
>$$
>where $A\in \mathbb{R}^{m\times n}$, $B\in \mathbb{R}^{m\times k}$.


## Explanation


## Solution

- [[Existence and Uniqueness of Solution of Linear Equations]]

## Normal Equation

![[Least Square Estimation Solution and Geometric Interpretation#^03c5db]]

- [[Least Square Estimation Solution and Geometric Interpretation]]


-----------
##  Recommended Notes and References

- [[Existence and Uniqueness of Solution of Linear Equations]]

- [[Range and Kernel of Linear Map]]
- [[Rank and Nullity of Linear Map]]
- [[Rank–Nullity Theorem]]

- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]


- [[Linear ODE with Constant Coefficients]]
- [[Linear Stochastic Differential Equation]]
- [[Homogeneous Linear Differential Equations]]



- [[Matrix Analysis by Horn]] pp 12
- [[Matrix Computations by Golub]]