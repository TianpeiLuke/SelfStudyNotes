---
tags:
  - concept
  - math/matrix_analysis
  - math/differential_equation
  - math/linear_algebra
  - math/differential_geometry
  - math/lie_group_algebra
keywords:
  - matrix_polynomial
topics:
  - matrix_analysis
  - differential_equation
name: Matrix Polynomial
date of note: 2024-10-14
---

## Concept Definition

>[!important]
>**Name**: Matrix Polynomial

>[!important] Definition
>Let $A\in M_{n}$ and  $p_{n}(x)$ be a *polynomial* of *degree* $n$, i.e. $$p_{n}(x) = x^n + a_{n-1}x^{n-1} \,{+}\ldots{+}\,a_{1}x + a_{0},$$ where $a_{i}\in F$ is some *field*.
>
>The **matrix polynomial** $p_{n}(A)$ is defined as 
>$$
>p_{n}(A) = A^n + a_{n-1}A^{n-1} \,{+}\ldots{+}\,a_{1}A + a_{0}I
>$$
>

- [[Polynomial Ring]]


>[!important] Proposition
>Let $A\in M_{n}$, $s, t\in \mathbb{R}$.
>
>- $$(p_{n}(A))^{*} = p_{n}(A^{*})$$
>	- This implies that $$A \text{ self-adjoint } \iff p_{n}(A) \text{ self-adjoint}$$
>- Any **polynomial** of $A$ commutes with** any **polynomial of $A$**, i.e. $$f(A)\,g(A) = g(A)\,f(A), \quad \forall f, g\in F[x]$$
>- For any $A, B\in M_{n}$ and any $f,\,g\in F[x]$, $$f(A)\,g(B) = g(B)\,f(A)$$ *if and only if* $A$ and $B$ **commute** i.e. $$AB = BA.$$


- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Laplace Transform]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Resolvent Operator and Spectrum of Linear Operator]]

### Schur Decomposition and Jordan Decomposition for Matrix Exponential

>[!important] Proposition
>If $A \in M_{n}$ is **self-adjoint (or normal)** with eigen-decomposition (**symmetric Schur form**) $$A = U\,\text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})\,U,$$ where $\lambda_{i}$ are **eigenvalues** of $A$,  then the **polynomial** of $A$ also has eigen-decomposition as  $$p_{n}(A) = U\,\text{diag}(p_{n}(\lambda_{1}) \,{,}\ldots{,}\, p_{n}(\lambda_{n})\,U^{T}$$ 
>

- [[Normal Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Schur Triangularization and Schur Form]]
- [[Positive Semidefinite Transformation]]


>[!info]
>If $$A = \sum_{i=1}^{n}\lambda_{i}u_{i}\,u_{i}^{*}$$ then $$p_{n}(A) = \sum_{i=1}^{n}p_{n}(\lambda_{i})\,u_{i}\,u_{i}^{*}$$


## Explanation


## Characteristic Polynomial

![[Cayley-Hamilton Theorem#^6f7d87]]

- [[Cayley-Hamilton Theorem]]
- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]


## Continuous Functional Calculus

![[Continuous Functional Calculus#^bc47ad]]

- [[Continuous Functional Calculus]]

## Circulant Matrix

- [[Circulant Matrix and Circulant Permutation Operation]]



-----------
##  Recommended Notes and References



- [[Matrix Exponential]]
- [[Exponential Map of Linear Operator]]
- [[Jordan Canonical Form]]
- [[Continuous Functional Calculus]]



- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Homogeneous Linear Differential Equations]]
- [[Linear Stochastic Differential Equation]]
- [[Linear Stochastic Differential Equation Explicit Solution]]


- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 109 - 114