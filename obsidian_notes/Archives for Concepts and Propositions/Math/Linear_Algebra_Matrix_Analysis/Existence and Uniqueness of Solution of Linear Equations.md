---
tags:
  - concept
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - linear_system
  - system_of_linear_equations
topics:
  - linear_algebra
name: System of Linear Equations Solution Space
date of note: 2024-09-15
---

## Concept Definition

>[!important]
>**Name**: System of Linear Equations Solution Space

![[System of Linear Equations or Linear System#^818e89]]

- [[System of Linear Equations or Linear System]]

### Consistent Linear System

>[!important] Definition
>- If the *system of linear equations* $$Ax = b$$ has *at least one solution*, then the linear system is said to be **consistent**. In other words, $$b \in \text{R}(A)$$
>- If the linear system has *no solution*, then the linear system is said to be **inconsistent**.

- [[Range and Kernel of Linear Map]]

### Augmented Matrix

>[!important] Definition
>For the linear system $$Ax = b,$$ the matrix $$\left[ A \;|\; b \right] \in M_{m, n+1}(F)$$ is called the **augmented matrix.**

>[!important] Proposition
>The **linear system** $$Ax = b$$ is **consistent** *if and only if* the **augmented matrix** and **coefficient matrix** has the **same rank** $$\text{rank}[A; b] = \text{rank}(A).$$

- [[Rank and Nullity of Linear Map]]


## Explanation


## Existence and Uniqueness of Solution of Linear System

>[!important] Theorem
>Consider the **system of linear equations** $$Ax = b$$ where $A\in \mathbb{R}^{m\times n}$, $b\in \mathbb{R}^{m}$
>- There **exists** a solution to above equations *if and only if* $$b\in \text{R}(A)$$
>- There **exists** a solution to above equations *if and only if* $$\text{R}(A) = \mathbb{R}^{m}$$ i.e. the linear map $A$ is **surjective.** 
>	- Equivalently, the **augmented matrix** and **coefficient matrix** has the **same rank** $$\text{rank}[A; b] = \text{rank}(A).$$
>	- This is possible *only if* $$\text{dim}(\text{R}(A)) = \text{rank}(A) = m \le n.$$
>- A solution to above equations is **unique** *if and only if* the **kernel space** $$\text{Ker}(A) = \mathcal{N}(A) = \{ 0 \},$$ i.e. $A$ is **injective**.
>- There **exists** a **unique** *solution* to above equations *for all* $b\in \mathbb{R}^{m}$ *if and only if* $A$ is **bijective** (**invertible**).
>	- Equivalently, $A\in \mathbb{R}^{m\times m}$ and $A$ has *neither*  *eigenvalue* $\lambda = 0$ nor *singular value* $\sigma = 0$
>- There exists **at most one solution** to above equations for all $b\in \mathbb{R}^{m}$ *if and only if*  the **columns** of $A$ are **linear independent**, i.e. $$\text{Ker}(A) = \{ 0 \}.$$
>	- This is only possible if $m \ge n$.
>- There exists a **nontrivial solution** to the **homogeneous system** $$Ax = 0$$ *if and only if* $$\text{rank}(A) < n.$$

- [[Range and Kernel of Linear Map]]
- [[Surjective Injective Invertible Linear Map and Rank]]

## Existence and Uniqueness of Solution for Matrix Linear System

>[!important] Theorem (Existence)
>The **matrix linear system** $$AX = B$$ where $A\in \mathbb{R}^{m\times n}$, $B\in \mathbb{R}^{m\times k}$ has a **solution** *if and only if* $$\text{R}(B) \subseteq \text{R}(A);$$
>- equivalently, a solution **exists** *if and only if* $$A\,A^{+}\,B = B.$$ Here $A^{\dagger}$ is the **Moore-Penrose pesudoinverse**.

- [[Moore–Penrose Pseudo Inverse of Matrix]]

>[!important] Theorem (Solution of Matrix Linear System)
>Let $A\in \mathbb{R}^{m\times n}$, $B\in \mathbb{R}^{m\times k}$ and *suppose* that $$A\,A^{+}\,B = B.$$
>
>Then any matrix of the **form** $$X = A^{+}\,B + \left(I - A^{+}\,A\right)\,Y$$
>where $Y\in \mathbb{R}^{n\times k}$ is *arbitrary* is a **solution** of $$A\,X = B.$$  Furthermore, **all solutions** of above matrix linear system are of this form.

^1dcd93

- [[Least Square Estimation Solution and Geometric Interpretation]]

![[Fundamental Orthogonal Projections#^64a8f0]]

![[Fundamental Orthogonal Projections#^3d1aa0]]

- [[Fundamental Orthogonal Projections]]

>[!important] Theorem (Uniqueness)
>A solution to the *matrix linear system* $$AX = B$$ where $A\in \mathbb{R}^{m\times n}$, $B\in \mathbb{R}^{m\times k}$ is **unique** *if and only if* $$A^{+}\,A = I;$$
>- equivalently, the above equation has a **unique solution** *if and only if* $$\text{Ker}(A) = \{ 0 \}.$$

- [[Fundamental Subspaces from Linear Map]]

## Linear Least Square Estimation

![[Least Square Estimation#^9775a7]]

![[Least Square Estimation Solution and Geometric Interpretation#^0bdae8]]

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]




-----------
##  Recommended Notes and References

- [[System of Linear Equations or Linear System]]

- [[Range and Kernel of Linear Map]]
- [[Rank and Nullity of Linear Map]]
- [[Rank–Nullity Theorem]]

- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]



- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]
- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]
- [[Linear Ordinary Differential Equations with Constant Coefficients]]
- [[Linear Stochastic Differential Equation]]
- [[Homogeneous Linear Differential Equations]]



- [[Matrix Analysis by Horn]] pp 12
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 43 - 46
- [[Matrix Computations by Golub]]
- [[Matrix CookBook by Petersen]] pp 28