---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - derogatory_matrix
  - nonderogatory_matrix
  - defective_matrix
  - nondefective_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Derogatory Matrix and Defective Matrix
date of note: 2024-10-04
---

## Concept Definition

>[!important]
>**Name**: Derogatory Matrix and Defective Matrix

![[Algebraic and Geometric Multiplicity of Linear Map#^7049c6]]

![[Algebraic and Geometric Multiplicity of Linear Map#^273395]]


>[!important] Definition
>Let $A\in M_{n}$ and the *charateristic polynomial* is $$\det \left(\lambda I - A\right) = \prod_{i=1}^{q}(\lambda - \lambda_{i})^{k_{i}}.$$
>
>- $A$ is said to be **defective** if the *geometric multiplicity* of *some eigenvalue* of $A$ is *strictly less than* its *algebraic multiplicity*. $$(\exists \lambda_{i}\in \lambda(A)) \quad \text{dim}(\mathcal{E}_{\lambda_{i}}) < k_{i}.$$
>- $A$ s said to be **nondefective** if the *geometric multiplicity* of *all eigenvalue* of $A$ is *the same as* its *algebraic multiplicity*.  $$(\forall \lambda_{i}\in \lambda(A)) \quad \text{dim}(\mathcal{E}_{\lambda_{i}}) = k_{i}.$$
>- $A$ is said to be **derogatory** if the *geometric multiplicity* of *some eigenvalue* of $A$ is *greater than* $1$. $$(\exists \lambda_{i}\in \lambda(A)) \quad \text{dim}(\mathcal{E}_{\lambda_{i}}) > 1.$$
>- $A$ is said to be **nonderogatory** if the *geometric multiplicity* of *all eigenvalue* of $A$ is *equal to* $1$. $$(\forall \lambda_{i}\in \lambda(A)) \quad \text{dim}(\mathcal{E}_{\lambda_{i}}) = 1.$$

^29fa19

- [[Algebraic and Geometric Multiplicity of Linear Map]]


## Explanation



## Diagonalizable

>[!important] Proposition
>A matrix $A$ is **diagonalizable** *if and only if* it is **nondefective**.
>
>$A$ has **distinct eigenvalues** *if and only if* it is **nonderogatory** and **nondefective**.

^872c76

- [[Diagonalizable Matrix]]

## Hessenberg Decomposition

![[Hessenberg Decomposition of Matrix#^49191f]]

![[Hessenberg Decomposition of Matrix#^f822a0]]

- [[Hessenberg Decomposition of Matrix]]

## Jordan Canonical Form

![[Jordan Canonical Form#^31139a]]

>[!important]
>A matrix $A$ is **nonderogatory** if its *Jordan canonical form* has **only one Jordan block** for *each eigenvalue*. That is, $$A \sim J_{q_{1}}(\lambda_{1})\,{\oplus}\ldots{\oplus}\,J_{q_{r}}(\lambda_{r}).$$

- [[Jordan Canonical Form]]
- [[Jordan Canonical Form Geometric Interpretation]]
- [[Similarity Relation between Linear Maps and Matrices]]





-----------
##  Recommended Notes and References


- [[Jordan Canonical Form]]
- [[Krylov Subspace and Krylov Matrix]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] 77, 106
- [[Matrix Computations by Golub]] pp 383