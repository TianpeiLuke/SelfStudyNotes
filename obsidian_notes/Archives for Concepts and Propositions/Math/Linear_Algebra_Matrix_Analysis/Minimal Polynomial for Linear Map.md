---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - minimal_polynomial
topics:
  - linear_algebra
  - matrix_analysis
name: Minimal Polynomial for Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Minimal Polynomial for Linear Map

![[Characteristic Polynomial for Linear Map#^785fd1]]

- [[Characteristic Polynomial for Linear Map]]



## Explanation


## Jordan Canonical Form

>[!important] Theorem
>Let  $A \in M_{n}$ be a given matrix whose **distinct eigenvalues** are $\lambda_{1} \,{,}\ldots{,}\,\lambda_{q}$.
>
>The **minimal polynomial** of $A$ is $$Q_{A}(\lambda) = \prod_{i=1}^{q}\left(\lambda - \lambda_{i}\right)^{r_{i}}$$ in which $r_{i}$ is the **size** of the **largest Jordan block** of $A$ corresponding to **eigenvalues** $\lambda_{i}.$

^5a01ca

- [[Jordan Canonical Form]]
- [[Eigenvalue and Eigenvector for Linear Map]]

## Diagonalizable Matrix

>[!important] Corollary
>Let  $A \in M_{n}$ be a given matrix whose **distinct eigenvalues** are $\lambda_{1} \,{,}\ldots{,}\,\lambda_{q}$ and let a *polynomial*  $$Q(\lambda) = \prod_{i=1}^{q}\left(\lambda - \lambda_{i}\right).$$
>
>Then $A$ is **diagonalizable** *if and only if* $$Q(A) = 0.$$

- [[Diagonalizable Matrix]]
- [[Cayley-Hamilton Theorem]]




-----------
##  Recommended Notes and References


- [[Annihilator of Subset of Vector Space]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Characteristic Polynomial for Linear Map]]

- [[Algebraic and Geometric Multiplicity of Linear Map]]

- [[Companion Matrix of Polynomial]]
- [[Linear Map]]
- [[Matrix]]


- [[Finite Dimensional Vector Spaces by Halmos]] pp 112 -- 115
- [[Matrix Analysis by Horn]] pp 191 - 195