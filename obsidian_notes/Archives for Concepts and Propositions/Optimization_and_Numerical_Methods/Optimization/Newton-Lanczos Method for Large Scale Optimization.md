---
tags:
  - concept
  - optimization/algorithm
  - optimization/theory
keywords:
  - inexact_newton_method
  - newton_lanczos
topics:
  - optimization/algorithm
name: Newton-Lanczos Method for Large Scale Optimization
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Newton-Lanczos Method for Large Scale Optimization

### Inexact Newton Methods

![[Newton-Conjugate Gradient and Inexact Newton Method#^85f6f1]]

- [[Newton-Conjugate Gradient and Inexact Newton Method]]
- [[Newton Method]]
- [[Normal Equations and Newton System of Equations]]

###  Newton-Lanczos Methods

>[!important] Definition
>Consider the task of solving a *large-scale optimization* $$\min f(x)$$ where $f$ is *twice continuous differentiable.*
>
>Then at iteration $k$, the **Newton-Lanczos algorithm** solves the Newton system $$B_{k}p_{k} = - \nabla f_{k}$$ on the *Krylov subspace*
>$$ 
> \begin{align*}
> \min_{p} \;&\;\; \frac{1}{2} p^{T}B_{k}p + \nabla f_{k}^{T}p\\
> \text{s.t. }\;&\; p \in p_{0} + \mathcal{K}(B_{k}, \nabla f_{k}, k)
>\end{align*}
> $$
> where
> - $$B_{k} = \nabla^2 f(x_{k}), \quad \nabla f_{k} = \nabla f(x_{k})$$
> - $$\mathcal{K}(B_{k}, \nabla f_{k}, k) := \text{span}\left\{ \nabla f_{k},\,B_{k}\nabla f_{k} \,{,}\ldots{,}\, B_{k}^{k-1}\nabla f_{k}\right\}$$
>
>And $$x_{k} = x_{k-1} + p_{k}$$
>
>Specifically, the *Lanczos iteration* reduce the Hessian $B_{k}$ into tridiagonal matrix $T_{k}$ in each iteration $k$ as $$T_{k} = Q_{k}^{T}B_{k}Q_{k}$$ where  $$T_{k} = \left[ \begin{array}{ccccc}\alpha_{1} & \beta_{1} & & 0 \\[5pt] \beta_{1} & \alpha_{2} & \ddots &   \\[5pt]   & \ddots & \ddots &   \beta_{k-1} \\[5pt]  &    & \beta_{k-1} & \alpha_{k}\end{array} \right]  \in \mathbb{R}^{k\times k}$$ and $Q_{k} = [q_{1}\,{,}\ldots{,}\,q_{k}]$ are the collection of *Lanczos vectors* at iteration $k$. 

^7b8062

- [[Normal Equations and Newton System of Equations]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Krylov Subspace Methods]]

>[!info]
>The objective function above can be reformulated as 
>$$ 
> \begin{align*}
> \phi(p)&:= \frac{1}{2} p^{T}B_{k} p + \nabla f_{k}^{T}p \\[5pt]
> &= \frac{1}{2}\left( p_{0} + Q_{k}y_{k} \right)^{T}B_{k}\left( p_{0} + Q_{k}y_{k} \right) + \nabla f_{k}^{T}\left( p_{0} + Q_{k}y_{k} \right)\\[5pt]
> &= \frac{1}{2}y^{T}(Q_{k}^{T}B_{k}Q_{k})y + y^{T}Q_{k}^{T}r_{0} + \phi(p_{0})\\[5pt]
> &= \frac{1}{2}y^{T}T_{k}y + y^{T}Q_{k}^{T}r_{0} + \phi(p_{0})
>\end{align*}
> $$
>where 
>- the *initial residual* $$r_{0} := \nabla f_{k}^{T}+ B_{k}p_{0}.$$
>- The solution of above quadratic programming is $$T_{k}\,y_{k} = -Q_{k}^{T}r_{0} =  -\lVert r_{0} \rVert\,e_{1}.$$ since $q_1 = r_{0} / \lVert r_{0} \rVert.$


>[!important]
>With *Lanczos iteration*, the *Newton system* $$B_{k}p = -\nabla f_{k}$$ has been transformed into the **tridiagonal system** $$T_{k}y_{k} = -\lVert r_{0} \rVert e_{1} := -\beta_{0}e_{1}$$ where $$r_{0} = \nabla f_{k} + B_{k}p_{0}, \quad \beta_{0} = \lVert r_{0} \rVert $$
>
>The **descent direction** for **Newton-Lanczos** is updated via $$p_{k} = p_{0} + Q_{k}y_{k}$$

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Conjugate Gradient Algorithm Lanczos]]

## Explanation


## MINRES

- [[Minimal Residuals Algorithm and MINRES]]

## Newton-CG and CG-Lanczos

- [[Iterative Methods to approximate Solution of Large-Scale Linear System]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Lanczos]]
- [[Conjugate Gradient Algorithm Nonlinear]]



-----------
##  Recommended Notes and References


- [[BFGS Algorithm]]
- [[Line Search Strategies for Optimal Stepsize]]



- [[Secant Equation and Quasi-Newton Methods]]
- [[System of Linear Equations or Linear System]]


- [[Primal-Dual Interior Point Method for Convex Optimization]]
- [[Barrier Method for Convex Optimization]]
- [[Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Function]]
- [[Positive Semidefinite Transformation]]
- [[Hermitian or Symmetric Matrix]]


- [[Numerical Optimization by Nocedal]] pp 175 - 176