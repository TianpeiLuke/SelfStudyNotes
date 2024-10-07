---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - newton_algorithm
topics:
  - optimization/algorithm
name: Newton's Method
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Newton's Method

![[Gradient Descent Algorithm#^613ed7]]

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *twice continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **Newton's methods** or **Newton algorithm** works as follows:
>
>0. Initiate with  $x_{0}$ and *convergence tolerance* $\epsilon >0$
>1. $k \leftarrow 0$
>2. While $\lVert \nabla f(x_{k}) \rVert > \epsilon$:
>	1. compute the **search direction** $$d_{k} = - \left( \nabla^2 f(x_{k}) \right)^{-1}\,\nabla f(x_{k})$$ where 
>	2. set new point via **generalized gradient descent** $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ where $\alpha_{k}$ is computed from a *line search procedure* to satisfies the *Wolfe conditions*
>	3. update index $k \leftarrow k+ 1.$   

- [[Gradient of Smooth Map]]
- [[Gradient Descent Algorithm]]
- [[Line Search Strategies for Optimal Stepsize]]



## Explanation

>[!info]
>Since the **Hessian matrix** $\nabla^2 f(x_{k})$ may **not always be positive definite**, $d_{k}$ may **not always be a descent direction**, and many of the ideas discussed so far in this chapter no longer apply.

- [[Numerical Optimization by Nocedal]]  pp 44
- [[Normal Equations and Newton System of Equations]]


## Numerical Solution for Newton System

- [[Normal Equations and Newton System of Equations]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Newton-Conjugate Gradient and Inexact Newton Method]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]



-----------
##  Recommended Notes and References



- [[Numerical Optimization by Nocedal]]  pp 44
- [[Nonlinear Programming by Bertsekas]] pp 26, 79, 88
- [[Convex Optimization Algorithms by Bertsekas]] pp 67
- [[Deep Learning by Goodfellow]] pp 303