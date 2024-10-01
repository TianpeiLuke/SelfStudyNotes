---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/stochastic_process
keywords:
  - perron_frobenius_theorem
  - irreducible_nonnegative_matrix
topics:
  - matrix_analysis
  - stochastic_process
name: Perron-Frobenius Theorem on Irreducible Nonnegative Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Perron-Frobenius Theorem on Irreducible Nonnegative Matrix

>[!important] Perron-Frobenius Theorem
>Let $A\in M_{n}$ be **irreducible** and **nonnegative**. Suppose that $n \ge 2$.
>
>Then
>- the **spectral radius** of $A$ is **positive** $$\rho(A) = \sup\left\{ |\lambda|: \lambda\in \sigma(A) \right\} > 0.$$ 
>- $\rho(A)$ is an **algebraically simple eigenvalue** of $A$, i.e. the *algebraic multiplicity* of $\rho(A)$ is **$1.$** $$\det \left(\lambda I - A\right) = (\lambda - \rho(A))\,p_{1}(\lambda).$$
>- there *exists* a **unique** *real vector* $x=(x_{1}\,{,}\ldots{,}\,x_{n})$ such that $$Ax = \rho(A)\,x$$ and $$\left\langle  e\,,\, x   \right\rangle = \sum_{i=1}^{n}x_{i} = 1.$$ Moreover, this vector is **positive** i.e. $x \succ 0.$
>- there *exists* a **unique** *real vector* $y=(y_{1}\,{,}\ldots{,}\,y_{n})$ such that $$y^{T}A = \rho(A)\,y^{T}$$ and $$\left\langle  x\,,\, y   \right\rangle = \sum_{i=1}^{n}x_{i}y_{i} = 1.$$ Moreover, this vector is **positive** i.e. $y \succ 0.$

- [[Spectral Radius of Linear Operator]]
- [[Resolvent Operator and Spectrum of Linear Operator]]
- [[Irreducible Nonnegative Matrix]]
- [[Algebraic and Geometric Multiplicity of Linear Map]]

>[!important] Definition
>Let $A\in M_{n}$ be **irreducible** and **nonnegative**. 
>
>Then 
>- the **(right) Perron vector** of $A$ is defined as the *right eigenvector* $x$ of $A$ associated with $A$'s *spectral radius* (*maximum eigenvalue*). By **Perron-Frobenius theorem**, $$Ax = \rho(A)x, \quad x\in \Delta_{n}.$$
>- And the **left Perron vector** of $A$ is defined as the *left eigenvector* $y$ of $A$ associated with $A$'s *spectral radius* (*maximum eigenvalue*). That is, $$y^{T}A = \rho(A)y^{T}, \quad y\succ 0, \; \left\langle  x\,,\,y \right\rangle = 1.$$



## Explanation

- [[Invariant Measure and Stationary Distribution]]
- [[Irreducibility of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]



-----------
##  Recommended Notes and References

- [[Nonnegative and Positive Matrix]]
- [[Nonnegative Matrix Factorization]]

- [[Matrix]]
- [[Positive Linear Functional]]
- [[Power Iteration to solve Eigenvalue Problem of General Matrix]]

- [[Optimal Transport in Discrete Setting]]
- [[Network Flow Problem as Linear Optimization]]
- [[Stochastic Matrix and Doubly Stochastic Matrix]]


- [[Matrix Analysis by Horn]] pp 534 - 537
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]]