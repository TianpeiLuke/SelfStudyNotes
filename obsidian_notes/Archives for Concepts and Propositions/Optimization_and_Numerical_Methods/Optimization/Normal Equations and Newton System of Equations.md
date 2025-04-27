---
tags:
  - concept
  - optimization/theory
  - optimization/convex_optimization
  - numerical_methods/numerical_linear_algebra
  - statistics/inference
  - normal_equation
  - Newton_system_of_equations
keywords:
  - normal_equation_least_square
  - netwon_system_equations
topics:
  - numerical_linear_algebra
  - statistics/inference
  - convex_analysis
  - optimization
name: Normal Equations and Newton System of Equations
date of note: 2024-10-06
---

## Concept Definition

>[!important]
>**Name**: Normal Equations and Newton System of Equations

>[!important] Definition
>Let $A\in \mathbb{R}^{m\times n}$ and $b\in \mathbb{R}^{m}$.
>
>The **normal equations** or the **Newton system of equations** is of the form
>$$
>A^{T}A\;x = A^{T}b
>$$
>- $$S = A^{T}A \succeq 0$$ is *symmetric positive semidefinite*.

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Space of Symmetric Positive Semidefinite Matrices]]

### Generalization in RKHS

![[Covariance Operator in Reproducing Kernel Hilbert Space#^5a6926]]

- [[Covariance Operator in Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]



## Explanation

### Least Square Estimation

- [[Least Square Estimation]]
- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]

### Normal Transformations

- [[Normal Transformation]]
- [[Range and Kernel of Product Map and Normal Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]

### Conditional Distribution of Gaussian 

- [[Marginal and Conditional Distribution of Gaussian]]
- [[Gaussian Random Vector]]



## Solving Newton System of Equations

### Hermitian / Symmetric Positive Definite System of Equations

- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[LDU Factorization of Symmetric Matrix]]

- [[Least Square Estimation with QR Factorization]]
- [[Least Square Estimation via Singular Value Decomposition]]
- [[Householder QR Factorization]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[Gram-Schmidt Orthogonalization]]

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

### Iterative Methods to Solve Large Symmetric PD System

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Minimal Residuals Algorithm and MINRES]]
- [[Conjugate Gradient Algorithm Linear]]




## Secant Equation

>[!info]
>In **Newton's method**, the gradient descent **direction**
>$$
>d_{t} = - \left( \nabla^2 f(x_{t}) \right)^{-1}\,\nabla f(x_{t})
>$$
>Thus the finding the direction $d_{t} = d$ is the *solution of linear system* $$\nabla^2 f(x_{t})\,d =  - \nabla f(x_{t}) \iff H_{t}\,d = - g_{t}$$ where
>-  $H_{t}$ and $g_{t}$ are **Hessian matrix** and **gradient** of $f$ at $x_{t}$ respectively  $$H_{t} := \nabla^2 f(x_{t}), \quad g_{t} := \nabla f(x_{t})$$
>- The linear system $$H_{t}\,d = - g_{t}$$ is a **symmetric positive semidefinite system**

- [[Gradient Descent Algorithm]]
- [[Newton Method]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]

![[Secant Equation and Quasi-Newton Methods#^035e08]]

- [[Secant Equation and Quasi-Newton Methods]]

![[BFGS Algorithm#^7f5c27]]

- [[BFGS Algorithm]]




-----------
##  Recommended Notes and References


- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[System of Linear Equations or Linear System]]

- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 462
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 65 - 67
- [[Matrix CookBook by Petersen]] pp 28
- [[Matrix Computations by Golub]] pp 303 - 334
- [[Numerical Linear Algebra by Trefethen]] pp 77 - 87
- [[Convex Optimization by Boyd]] pp 458, 510
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]] pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245 - 269
- [[Elements of Statistical Learning by Hastie]] pp 12, 43 - 56