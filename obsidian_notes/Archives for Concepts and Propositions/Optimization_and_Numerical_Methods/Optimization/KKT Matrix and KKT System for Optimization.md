---
tags:
  - concept
  - optimization/convex_optimization
  - optimization/theory
  - numerical_methods/numerical_linear_algebra
keywords:
  - kkt_system
  - kkt_matrix
topics:
  - convex_analysis
  - optimization/theory
  - numerical_linear_algebra
name: KKT System for Optimization
date of note: 2024-10-08
---

## Concept Definition

>[!important]
>**Name**: KKT System for Optimization

![[System of Linear Equations or Linear System#^818e89]]

![[Karush-Kuhn-Tucker Optimality Condition#^a09722]]


>[!important] Definition
>A matrix has the **Karush-Kuhn-Tucker (KKT) structure** if it is of the form
>$$
>\left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>$$
>where 
>- $H\in \mathcal{S}_{++}^{p}$ is *positive definite*
>- $A\in \mathbb{R}^{p\times m}$ with *full column rank*, i.e. $\text{rank}(A) = m$.
>  
>The **KKT system of equations** is of the form  
>$$
>\left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>\left[ \begin{array}{c}
> x  \\[5pt]
> b 
>\end{array} \right] = 
>-\left[ \begin{array}{c}
>  g \\[5pt]
>  h
>\end{array}\right]
>$$


- [[System of Linear Equations or Linear System]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Positive Semidefinite Transformation]]

![[Schur Complement and Inversion of Block Matrix#^eb8bd3]]


>[!important] Proposition
>If  a *symmetric matrix* $\tilde{H} \in \mathcal{S}^{m+p}$ has **KKT structure**
>$$
>\widetilde{H} = \left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>$$
>where $H\in \mathcal{S}_{++}^{m}$ and $A\in \mathbb{R}^{p\times m}$ with full column rank, then the **Schur complement** of $H$ of $\widetilde{H}$ is **negative definite**
>$$
>S := \widetilde{H} / H := - A^{T}H^{-1}A \prec 0
>$$
>or $$- \widetilde{H} / H \in \mathcal{S}_{++}^{m}$$

- [[Schur Complement and Inversion of Block Matrix]]

>[!info]
>We can find **Cholesky factorization** of $\widetilde{H} / H$
>$$
>\widetilde{H} / H = GG^{T}
>$$
>where $G\in \mathbb{R}^{m\times m}$ is **lower triangular**.

- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Triangular Matrix and Block Triangular Matrix]]

## Explanation


### KKT System in Quadratic Programming with Equality Constraint

![[Quadratic Programming#^387671]]

- [[Quadratic Programming]]

### KKT System in Optimization with Equality Constraint





## KKT System in Gaussian Belief Propagation

![[Gaussian Belief Propagation#^919312]]

![[Gaussian Belief Propagation#^967ffd]]

- [[Gaussian Belief Propagation]]



-----------
##  Recommended Notes and References



- [[Sequential Quadratic Programming]]

- [[Convex Optimization Problem]]
- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Least Square Estimation]]
- [[Normal Equations and Newton System of Equations]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]


- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Schur Complement and Inversion of Block Matrix]]


- [[Gaussian Belief Propagation]]



- [[Numerical Optimization by Nocedal]] pp 275
- [[Convex Optimization by Boyd]]  pp 542 - 547, 677
