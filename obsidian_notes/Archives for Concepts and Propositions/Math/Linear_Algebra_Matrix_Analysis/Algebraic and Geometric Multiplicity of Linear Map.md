---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - algebraic_multiplicity_linear_map
  - geometric_multiplicity_linear_map
topics:
  - linear_algebra
name: Algebraic and Geometric Multiplicity of Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Algebraic and Geometric Multiplicity of Linear Map

![[Characteristic Polynomial for Linear Map#^785fd1]]

### Algebraic Multiplicity

>[!important] Definition
>Let $A\in M_{n}$.
>
>The **multiplicity** of an *eigenvalue* $\lambda$ of $A$ is its multiplicity as a zero of the characteristic polynomial $P_{A}(\lambda)$. That is,
>$$
>P_{A}(\lambda) = \prod_{i=1}^{q}\left(\lambda - \lambda_{i}\right)^{k_{i}}
>$$
>where $$\sum_{i=1}^{q}k_{i} = n.$$ Then $k_{i}$ is the  *multiplicity of an eigenvalue* $\lambda_{i}$.
>
>For clarity, we sometimes refer to the *multiplicity of an eigenvalue* as its **algebraic multiplicity**.
>$$
>\text{algebraic multiplicity}(\lambda_{i}) := k_{i}
>$$ 


^7049c6

- [[Characteristic Polynomial for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]

### Geometric Multiplicity

![[Eigenspace and Spectrum for Linear Map#^1372fd]]

>[!important] Definition
>Let $A\in M_{n}$ and $\lambda$ be an *eigenvalue* of $A$.
>
>The **geometric multiplicity** of an *eigenvalue* $\lambda$ of $A$ is the *dimension of the eigenspace associated with* $\lambda$
>$$
>\text{geometric multiplicity}(\lambda) := \text{dim}\left(\mathcal{E}_{\lambda}\right)
>$$ 

- [[Eigenspace and Spectrum for Linear Map]]


## Explanation

>[!quote]
>the **eigenvalues** of $A \in M_n$ will always mean the **eigenvalues** *together with* their **respective (algebraic) multiplicities**.




>[!important] Theorem
>The **geometric multiplicity** of an **eigenvalue** $\Lambda$ of $A \in L(V)$ is **less than or equal to** its **algebraic multiplicity**.
>
>$$
>\text{geometric multiplicity}(\lambda) := \text{dim}\left(\mathcal{E}_{\lambda}\right) \le \text{algebraic multiplicity}(\lambda)
>$$ 



## Jordan Form




-----------
##  Recommended Notes and References

- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Linear Map]]



- [[Finite Dimensional Vector Spaces by Halmos]] pp 112 -- 115
- [[Matrix Analysis by Horn]] pp 49 - 56, 75 - 82
- [[Matrix Analysis for Scientists and Engineers by Laub]]