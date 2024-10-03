---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - eigen_value
  - eigen_vector
topics:
  - linear_algebra
  - functional_analysis
name: Eigenvalue and Eigenvector for Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Eigenvalue and Eigenvector for Linear Map

>[!important] Definition
>Let $V$ be a vector space over field $F$ and let $A \in \mathcal{L}(V)$ be a linear transformation on $V$.
>
>A scalar $\lambda \in F$ is an **eigenvalue** or **characteristic value** of $A$ if there *exists* a *nonzero* vector $v\in V$ such that 
>$$
>A\,v = \lambda\,v
>$$
>
>In this case, the vector $v$ is called an **(right) eigenvector** or **characteristic vector** of $A$ *associated with* $\lambda.$

^06f8b9

- [[Vector Space over a Field]]

>[!important] Definition
>Let $V$ be a vector space over field $F$, $V^{*}$ be the *dual space* of $V$. 
>
>Let $A \in \mathcal{L}(V)$ be a linear transformation on $V$ and $A^{*}\in \mathcal{L}(V^{*})$ be the *adjoint* of $A$
>
>
>A nonzero *covector* $f\in V^{*}$ is called a **left (right) eigenvector** of $A$ *associated with* eigenvalue $\lambda$ if $$A^{*}f = \bar{\lambda}\,f$$ or equivalently, the dual of $f$, $f^{*}$ satisfies $$f^{*}\,A = \lambda\,f^{*}.$$

- [[Adjoint of Linear Map]]


>[!important] Definition (Matrix)
>A scalar $\lambda \in F$ is an **eigenvalue** or **characteristic value** of a matrix $\boldsymbol{A}$ if there *exists* a *nonzero* (column) vector $\boldsymbol{v}$ such that 
>$$
>\boldsymbol{A\,v} = \lambda\, \boldsymbol{v}
>$$
>
>In this case, the vector $\boldsymbol{v}$ is called an **(right) eigenvector** or **characteristic vector** of $\boldsymbol{A}$ *associated with* $\lambda.$

^1b8cf8

>[!important] Definition (Matrix)
>A nonzero vector $w\in \mathbb{C}^{n}$ is a **left eigenvector** of $A\in M_{n}$ associated with an **eigenvalue** $\lambda\in \mathbb{C}$ of $A$ if $$w^{*}A = \lambda\,w^{*}.$$
>

^bec9fb

 
## Explanation

>[!important]
>$\lambda$ is an eigenvalue of $A$ if and only if the matrix
>$$
>(\lambda I - A)
>$$
>is **not invertible**.

- [[Resolvent Operator and Spectrum of Linear Operator]]

>[!important]
>Eigenvalue $\lambda$ of $A$ is a *root* of the **characteristic equation**
>$$
>\det \left(\lambda I - A\right) = 0
>$$

^fb9212

- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]

### Trace and Determinant in terms of Eigenvalue

- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]

### Geometric Multiplicity

- [[Algebraic and Geometric Multiplicity of Linear Map]]

## Invariance Under Similarity Relation

>[!important] Theorem
>Let $A, B\in M_{n}$ and suppose that $$B = S^{-1}AS$$ for some nonsingular $S$ ($A \sim B$).
>
>- If $x\in \mathbb{C}^{n}$ is a **right eignvector** of $B$ associated with an **eigenvalue** $\lambda$, then $$Sx$$ is a **right eigenvector** of $A$ associated with the same **eigenvalue** $\lambda$.
>- If $y\in \mathbb{C}^{n}$ is a **left eignvector** of $B$ associated with an **eigenvalue** $\lambda$, then $$(S^{*})^{-1}y$$ is a **left eigenvector** of $A$ associated with the same **eigenvalue** $\lambda$.

^1a14c3

- [[Similarity Relation between Linear Maps and Matrices]]



## Canonical Forms

- [[Schur Triangularization and Schur Form]]
- [[Jordan Canonical Form]]

## Spectral Theorem

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]


## Principle of Biorthogonality

- [[Principle of Biorthogonality]]


## Singular Value and Singular Value Decomposition

- [[Singular Value Decomposition of Linear Map]]



-----------
##  Recommended Notes and References

- [[Characteristic Polynomial for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 75 - 80
- [[Matrix CookBook by Petersen]] pp 30