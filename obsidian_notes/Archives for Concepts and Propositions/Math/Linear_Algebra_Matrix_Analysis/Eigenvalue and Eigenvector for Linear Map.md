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
>In this case, the vector $v$ is called an **eigenvector** or **characteristic vector** of $A$ *associated with* $\lambda.$

^06f8b9

- [[Vector Space over a Field]]

>[!important] Definition (Matrix)
>A scalar $\lambda \in F$ is an **eigenvalue** or **characteristic value** of a matrix $\boldsymbol{A}$ if there *exists* a *nonzero* (column) vector $\boldsymbol{v}$ such that 
>$$
>\boldsymbol{A\,v} = \lambda\, \boldsymbol{v}
>$$
>
>In this case, the vector $\boldsymbol{v}$ is called an **(right) eigenvector** or **characteristic vector** of $\boldsymbol{A}$ *associated with* $\lambda.$

>[!important] Definition
>A nonzero vector $w\in \mathbb{C}^{n}$ is a **left eigenvector** of $A\in M_{n}$ associated with an **eigenvalue** $\lambda\in \mathbb{C}$ of $A$ if $$w^{*}A = \lambda\,w^{*}.$$
>
 


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


## Trace and Determinant in terms of Eigenvalue

- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]


## Geometric Multiplicity

- [[Algebraic and Geometric Multiplicity of Linear Map]]


## Principle of Biorthogonality

- [[Principle of Biorthogonality]]
- [[Biorthogonalization Methods]]


-----------
##  Recommended Notes and References

- [[Characteristic Polynomial for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 75 - 80