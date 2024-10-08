---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/convex_optimization
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
> \min_{x\in \mathcal{X} \subset \mathbb{R}^{n}}&\; \frac{1}{2} \left\langle  x\,,\,Q x \right\rangle + \left\langle  c\,,\,x  \right\rangle \\[5pt]
>\text{s.t. } &Ax \preceq b
>\end{align*}
>$$
>where 
>- $Q \in \mathbb{R}^{n\times n}$ is *symmetric*
>- $A\in \mathbb{R}^{m\times n}$
>- $c\in \mathbb{R}^{n}$ and $b\in \mathbb{R}^{m}$.
>  
>If $Q \succ 0$ is *symmetric positive definite*, then the corresponding quadratic programming is **convex**.  

- [[Convex Optimization Problem]]
- [[Sesquilinear Form]]
- [[Multilinear Function]]
- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Convex Function]]

## Explanation

>[!quote]
>Ye and Tse [7](https://en.wikipedia.org/wiki/Quadratic_programming#cite_note-7) present a polynomial-time algorithm, which extends [Karmarkar's algorithm](https://en.wikipedia.org/wiki/Karmarkar%27s_algorithm "Karmarkar's algorithm") from linear programming to convex quadratic programming. On a system with $n$ *variables* and $L$ *input bits*, their algorithm requires $O(L n)$ iterations, each of which can be done using $O(L n^3)$ arithmetic operations, for a **total runtime complexity** of $O(L^2 n^4)$.
>
>Kapoor and Vaidya[8](https://en.wikipedia.org/wiki/Quadratic_programming#cite_note-8) present another algorithm, which requires $O(L * log L * n^{3.67} * log\,n)$ arithmetic operations.
>
>-- Wikipedia [Quadratic_programming](https://en.wikipedia.org/wiki/Quadratic_programming)

### Indefinite Quadratic Programming

- [[Integer Programming Problem]]



## Examples

### Least Square Estimation

![[Least Square Estimation#^9775a7]]

![[Least Square Estimation#^f8f306]]

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Normal Equations and Newton System of Equations]]
- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation with QR Factorization]]

### Conjugate Gradient Algorithm

- [[Conjugate Gradient Algorithm Linear]]


### Support Vector Machines

![[Support Vector Machine Linear Separable Case#^ad85f3]]

- [[Support Vector Machine Linear Separable Case]]

![[Support Vector Machine General with Soft-Margin Relaxation#^5c5e42]]

- [[Support Vector Machine General with Soft-Margin Relaxation]]




-----------
##  Recommended Notes and References


- [[Sequential Quadratic Programming]]




- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]
- [[Convex Optimization for Eigenvalue Problem]]


- [[Convex Optimization by Boyd]]
- [[Convex Optimization Algorithms by Bertsekas]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]