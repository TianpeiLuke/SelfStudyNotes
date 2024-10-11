---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/convex_optimization
  - numerical_methods/numerical_linear_algebra
keywords:
  - quadratic_programming
topics:
  - optimization
name: Quadratic Programming
date of note: 2024-10-06
---

## Concept Definition

>[!important]
>**Name**: Quadratic Programming


![[Convex Optimization Problem#^bc3f9c]]

>[!important] Definition
>A **quadratic programming (QP)** problem is defined as follow:
>$$
>\begin{align*}
> \min_{x\in \mathbb{R}^{n}}&\; \frac{1}{2} \left\langle  x\,,\,Q x \right\rangle + \left\langle  c\,,\,x  \right\rangle \\[5pt]
>\text{s.t. } &Ax \preceq b
>\end{align*}
>$$
>where 
>- $Q \in \mathbb{R}^{n\times n}$ is *symmetric*
>- $A\in \mathbb{R}^{m\times n}$
>- $c\in \mathbb{R}^{n}$ and $b\in \mathbb{R}^{m}$.
>- That is, the objective function is *quadratic*, and the constraints are *affine*. We minimize a quadratic function over a *polyhedron*.
>  
>If $Q \succ 0$ is *symmetric positive definite*, then the QP is called **convex quadratic programming.** We can convert the *convex quadratic programming* into a **constrained least square** problem
>$$
>\begin{align*}
> \min_{x\in  \mathbb{R}^{n}}&\; \frac{1}{2}\lVert Rx - d \rVert_{2}^2  \\[5pt]
>\text{s.t. } &Ax \preceq b
>\end{align*}
>$$ 
>where
>- $R$ is the *Cholesky factorization* of $Q$ $$R^{T}R = Q.$$ 
>- and $$c = -R^{T}d.$$
>

^9ccf19

- [[Convex Optimization Problem]]
- [[Sesquilinear Form]]
- [[Multilinear Function]]

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Convex Function]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]



### QP with Equality Constraints

>[!important] Definition
>A **quadratic programming (QP)** problem is easy if $Q \succ 0$ is *symmetric positive definite*, and the constraints are the *equality constraints*
>$$
>\begin{align*}
> \min_{x\in \mathcal{X} \subset \mathbb{R}^{n}}&\; \frac{1}{2} \left\langle  x\,,\,Q x \right\rangle + \left\langle  c\,,\,x  \right\rangle \\[5pt]
>\text{s.t. } &Ex = d.
>\end{align*}
>$$
>- The *Lagrangian* is $$L(x, \lambda) = \frac{1}{2} \left\langle  x\,,\,Q x \right\rangle + \left\langle  c\,,\,x  \right\rangle + \left\langle  \lambda\,,\,   Ex - d \right\rangle$$
>- Based on the *KKT conditions*, the solution to the QP is the solution to a **symmetric positive definite linear system** $$\left[ \begin{array}{cc}Q & E^{T} \\[5pt] E & 0\end{array} \right]\;\left[ \begin{array}{c} x \\[5pt] \lambda \end{array} \right] = \left[ \begin{array}{c} -c \\[5pt] d\end{array} \right] $$
>- The symmetric positive definite system of equations can be solved numerically with *tridiagonal factorization*

^387671

- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]

![[KKT Matrix and KKT System for Optimization with Equality Constraints#^f43071]]




## Explanation

>[!quote]
>Ye and Tse [7](https://en.wikipedia.org/wiki/Quadratic_programming#cite_note-7) present a polynomial-time algorithm, which extends [Karmarkar's algorithm](https://en.wikipedia.org/wiki/Karmarkar%27s_algorithm "Karmarkar's algorithm") from linear programming to convex quadratic programming. On a system with $n$ *variables* and $L$ *input bits*, their algorithm requires $O(L n)$ iterations, each of which can be done using $O(L n^3)$ arithmetic operations, for a **total runtime complexity** of $O(L^2 n^4)$.
>
>Kapoor and Vaidya[8](https://en.wikipedia.org/wiki/Quadratic_programming#cite_note-8) present another algorithm, which requires $O(L * log L * n^{3.67} * log\,n)$ arithmetic operations.
>
>-- Wikipedia [Quadratic_programming](https://en.wikipedia.org/wiki/Quadratic_programming)

### Indefinite Quadratic Programming

- [[Integer Programming Problem]]


## Algorithms that Solve QP

### Generic Convex Programming Solver

- [[Primal-Dual Interior Point Method for Convex Optimization]]

### Iterative Optimization Solver

- [[Gradient Descent Algorithm]]
- [[Newton Method]]
- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]
- [[Trust Region Method]]

### Proximal Algorithms

- [[Augmented Lagrangian Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]
- [[Gradient Projection Method]]

### Symmetric Positive Definite Linear System Solver

- [[LDU Factorization of Symmetric Matrix]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Conjugate Gradient Algorithm Linear]]

### Iterative Solution to KKT System

- [[GMRES as Regression on Krylov Space]]




## Examples

### Least Square Estimation

![[Least Square Estimation#^9775a7]]

![[Least Square Estimation#^f8f306]]

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Normal Equations and Newton System of Equations]]
- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation with QR Factorization]]

- [[LASSO and Sparsity-Induced Least Square]]
- [[Ridge Regression and L2 Regularization]]

### Support Vector Machines

![[Support Vector Machine Linear Separable Case#^ad85f3]]

- [[Support Vector Machine Linear Separable Case]]

![[Support Vector Machine General with Soft-Margin Relaxation#^5c5e42]]

- [[Support Vector Machine General with Soft-Margin Relaxation]]

### Principle Component Analysis

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]
- [[Convex Optimization for Eigenvalue Problem]]
- [[Principle Component Analysis]]



## Second-Order Cone Programming

- [[Second-Order Cone Programming]]




-----------
##  Recommended Notes and References


- [[Sequential Quadratic Programming]]
- [[Applications involve System of Linear Equations]]




- [[Polyhedron and Polytope]]


- [[Convex Optimization by Boyd]] pp 152
- [[Convex Optimization Algorithms by Bertsekas]] pp 21, 483
- [[Numerical Optimization by Nocedal]] pp 422,  448 - 492
- [[Nonlinear Programming by Bertsekas]] pp 202, 256, 365, 385, 471, 600
- [[Matrix Computations by Golub]] pp 313 - 318
- Wikipedia [Quadratic_programming](https://en.wikipedia.org/wiki/Quadratic_programming)