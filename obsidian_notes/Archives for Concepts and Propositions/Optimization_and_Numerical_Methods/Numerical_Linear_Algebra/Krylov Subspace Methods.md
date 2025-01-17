---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - krylov_subspace
  - krylov_subspace_methods
topics: 
name: Krylov Subspace Methods
date of note: 2024-10-04
---

## Concept Definition

>[!important]
>**Name**: Krylov Subspace Methods


![[Krylov Subspace and Krylov Matrix#^27eea3]]

![[Nilpotent Linear Transformation and Matrix#^a1b57c]]

![[Nilpotent Linear Transformation and Matrix#^ee0cec]]

### Linear Regression on Krylov Subspaces

>[!important] Definition
>The **Krylov subspace methods** solve the *least square estimation* $$\min_{x} \lVert Ax - b \rVert_{2}^2$$  on an increasing sequence of *nested* *Krylov subspaces* generated by $A$ and $b$ $$\mathcal{K}_{1} \subset \mathcal{K}_{2} \,{\subset}\ldots{\subset}\,\mathcal{K}_{t}.$$
>
> That is, at each iteration $t$, **Krylov subspace methods** solve
> $$ 
> \begin{align*}
> \min_{x} \;&\;\; \lVert Ax - b \rVert_{2}^2\\
> \text{s.t. }\;&\; x \in x_{0} + \mathcal{K}(A, b, t)
>\end{align*}
> $$

^d69683

- [[Krylov Subspace and Krylov Matrix]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Nilpotent Linear Transformation Geometric Characterization]]
- [[Linear Regression]]
- [[Least Square Estimation]]


### Best Polynomial Approximation

>[!important] Definition
>Let $p_{n}(x)$ be a *polynomial* of *degree* $n$, i.e. $$p_{n}(x) = x^n + a_{n-1}x^{n-1} \,{+}\ldots{+}\,a_{1}x + a_{0},$$ where $a_{i}\in F$ is some *field*. Let $F_{n}[x]$ denote the space of all  *polynomials* of *degree* less than or equal to $n$
>$$F_{n}[x] = \left\{ p(x): \text{ degree of }p \le n \right\} $$
>
>The **polynomial of linear map** $A\in L(V)$ is defined as $$p_{n}(A) = A^n + a_{n-1}A^{n-1} \,{+}\ldots{+}\,a_{1}A + a_{0}I.$$
>- This is the *image of a mapping* $$F[\lambda(A)] \to L(V): \quad p_{n}(x) \mapsto B := p_{n}(A)$$
>- The *spectrum* of $p_{n}(A)$ is $$\lambda_{i} \in \lambda(A) \quad \implies \quad p_{n}(\lambda) \in \lambda(p_{n}(A))$$
>
>The **Krylov subspace methods** can be considered as the finding the **optimal polynomial** $p(x) \in F_{n}[x]$ such that the **norm** of **polynomial approximation** of $A$ over $b$  is minimized
>$$
>\min_{p \in F_{n}[x], \; p(0) = 1}  \;\lVert p(A)b \rVert_{2}^2 
>$$

^2c2024

- [[Continuous Functional Calculus]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Polynomial Ring]]


## Explanation

![[krylov_subspace_methods_classification.png]]


### Hessenberg Orthogonalization

- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[GMRES as Regression on Krylov Space]]

### Tridiagonal Orthogonalization

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Lanczos Iteration Practical with Reorthogonalization]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Lanczos]]
- [[Minimal Residuals Algorithm and MINRES]]


### Tridiagonal Bi-Orthogonalization

- [[Normal Equations and Newton System of Equations]]
- [[Biorthogonalization Methods]]
- [[Conjugate Gradient Normal Equation Residual and CGNR]]
- [[Biconjugate Gradients Algorithm for Nonsymmetric System]]



-----------
##  Recommended Notes and References



- [[Least Square Estimation with QR Factorization]]

- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[Gram-Schmidt Orthogonalization]]

- [[Sequential Quadratic Programming]]

- [[Matrix Analysis by Horn]] 
- [[Numerical Linear Algebra by Trefethen]] pp 266 -275
- [[Matrix Computations by Golub]] pp 644 - 645