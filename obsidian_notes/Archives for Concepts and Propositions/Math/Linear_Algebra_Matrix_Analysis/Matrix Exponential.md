---
tags:
  - concept
  - math/matrix_analysis
  - math/differential_equation
  - math/linear_algebra
  - math/differential_geometry
  - math/lie_group_algebra
keywords:
  - matrix_exponential
topics:
  - matrix_analysis
  - differential_equation
name: Matrix Exponential
date of note: 2024-10-14
---

## Concept Definition

>[!important]
>**Name**: Matrix Exponential

>[!important] Definition
>Let $A\in M_{n}$.
>
>The **matrix exponential** of $A$ is defined to be the *series* 
>$$
>e^{A} \equiv \exp(A) = \sum_{k=0}^{\infty} \frac{1}{k!}A^{k}
>$$
>- The series *converges to all* $A$, i.e. with radius of convergence for $|\lambda(A)| \leq \infty.$


## Explanation

### Lie Group and Lie Algebra



- [[Exponential Map via Geodesic on Riemannian Manifold]]
- [[Lie Group]]
- [[Lie Algebra as Vector Space with Lie Bracket]]


## Properties

>[!important] Proposition
>Let $A\in M_{n}$, $s, t\in \mathbb{R}$.
>
>- For $0\in \mathbb{R}^{n\times n}$, $$e^{0} = I$$
>- $$\exp(I) = \sum_{k=0}^{\infty} \frac{1}{k!} = e.$$
>- $$(e^{A})^{*} = e^{A^{*}}$$
>	- This implies that $$A \text{ self-adjoint } \iff e^{A} \text{ self-adjoint}$$
>- For any $t$, $e^{tA}$ **commutes with** any **polynomial of $A$**, i.e. $$e^{tA}\,p(A) = p(A)\,e^{tA}, \quad \forall p\in F[x]$$
>- For any $A\in M_{n}$ and any $s,t \in \mathbb{R}$, we have $$e^{(t+s)A} = e^{tA}\,e^{sA} = e^{sA}\,e^{tA}.$$ That is, $e^{tA}$ and $e^{sA}$ **commute.**
>- For any $A, B\in M_{n}$ and any $t\in \mathbb{R}$, $$e^{t(A+B)} = e^{tA}e^{tB} = e^{tB}e^{tA}$$ *if and only if* $A$ and $B$ **commute** i.e. $$AB = BA.$$
>- For any $A\in M_{n}$ and all $t$, $\exp(tA)$ is **nonsingular** and $$(e^{tA})^{-1} = e^{-tA}.$$
>- Let $\mathcal{L}$ be the **Laplace transform operator**. Then $$\mathcal{L}\left( \exp(\lambda A) \right) = (\lambda I- A)^{-1}$$ where $\lambda\not\in \lambda(A)$ is *not in the spectrum* of $A$ and $$(\lambda I- A)^{-1}$$ is called the **resolvent** of $A$.
>- The **derivative** of $e^{tA}$ with *respect to* $t$ is $$\frac{d}{dt} e^{tA} = A\,e^{tA} = e^{tA}\,A.$$

- [[Matrix Polynomial]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Laplace Transform]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Resolvent Operator and Spectrum of Linear Operator]]

## Schur Decomposition and Jordan Decomposition for Matrix Exponential

>[!important] Proposition
>If $A \in M_{n}$ is **self-adjoint (or normal)** with eigen-decomposition (**symmetric Schur form**) $$A = U\,\text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})\,U,$$ where $\lambda_{i}$ are **eigenvalues** of $A$,  then the **exponential** of $A$ also has eigen-decomposition as  $$e^{A} = U\,\text{diag}(e^{\lambda_{1}} \,{,}\ldots{,}\, e^{\lambda_{n}})\,U^{T}$$ 
>
>This implies that $$A \text{ normal (or Hermitian) } \implies e^{tA} \succeq\,0$$

- [[Normal Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Schur Triangularization and Schur Form]]
- [[Positive Semidefinite Transformation]]

>[!info]
>If $$A = \sum_{i=1}^{n}\lambda_{i}u_{i}\,u_{i}^{*}$$ then $$e^{tA} = \sum_{i=1}^{n}e^{t\lambda_{i}}\,u_{i}\,u_{i}^{*}$$

## Determinant

>[!important] Proposition
>For any $X\in M_{n}(\mathbb{C})$, we have 
>$$
>\det \left(e^{X}\right) = e^{\text{tr}(X)}
>$$

- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]


## Polar Decomposition

![[Polar Decomposition of Transformation#^636e45]]

>[!important] Proposition
>Let $P\in M_{n}$ be a **self-adjoint**, **positive definite transformation**. 
>
>Then $P$ can be **uniquely** written as a **matrix exponential** $$P = e^{X}$$ where $X \in M_{n}$ is **self-adjoint** linear transformation. 
>
>- Conversely, if $X\in M_{n}$ is **self-adjoint**, then $$e^{X} \in \mathcal{S}_{++}^{n}$$ is a *self-adjoint*, *positive definite*. 

>[!important] Proposition
>For $A\in \text{GL}(n)$, there exists a **unique decomposition** $$A  = Ue^{X}$$ where $U$ is *unitary* and $X$ is *self-adjoint*.

- [[Positive Semidefinite Transformation]]
- [[Self-Adjoint Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Polar Decomposition of Transformation]]


## Global Flow in General Linear Group

![[Matrix Exponential as Global Flow in General Linear Group#^926b51]]

![[Matrix Exponential as Global Flow in General Linear Group#^b0ad7e]]

- [[Matrix Exponential as Global Flow in General Linear Group]]

## Exponential Map on Matrix Lie Group

![[Exponential Map of Lie Group and Matrix Lie Group#^c127f2]]

![[Exponential Map of Lie Group and Matrix Lie Group#^910d1c]]

- [[Exponential Map of Lie Group and Matrix Lie Group]]




-----------
##  Recommended Notes and References


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
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 31 - 45
- [[Introduction to Smooth Manifolds by Lee]] pp 517