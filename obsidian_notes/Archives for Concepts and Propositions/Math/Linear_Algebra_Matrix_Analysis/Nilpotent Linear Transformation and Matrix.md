---
tags:
  - concept
  - math/linear_algebra
keywords:
  - nilpotent_matrix
  - nilpotent_linear_transform
topics:
  - algebra
name: Nilpotent Linear Transformation and Matrix
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Nilpotent Linear Transformation and Nilpotent Matrix

>[!important] Definition
>A linear transformation $A$ is called **nilpotent** if there exists some $m\in \mathbb{N}$ such that $$A^m = 0.$$
>
>The least such integer $m$ is called the **index of nilpotence**.

^a1b57c


>[!important] Definition
>A matrix $\boldsymbol{A}$ is called **nilpotent matrix** if there exists some $m\in \mathbb{N}$ such that $$\boldsymbol{A}^m = 0.$$

- [[Nilpotent Element in Ring]]
## Explanation



## Property

>[!important] Proposition
>If $A$ is a **nilpotent linear transformation** of *index* $m$ on a finite dimensional vector space $V$, and if $x_{0} \in V$ is a vector for which $$A^{m-1}x_{0} \neq 0,$$
>then  the vectors
>$$
>x_{0}, Ax_{0} \,{,}\ldots{,}\, A^{m-1}x_{0}
>$$
>are **linearly independent.**
>
>If $S$ is a *vector space spanned by* these vectors, $$S = \text{span}\{ x_{0},\, Ax_{0} \,{,}\ldots{,}\, A^{m-1}x_{0} \},$$ then there *exists a subspace* $W$ such that
>$$
>V = S \oplus W
>$$ 
>and such that the pair $(S, W)$  **reduces** $A$

^ee0cec

- [[Linear Independence]]
- [[Linear Subspace]]
- [[Direct Sum of Subspaces]]
- [[Vector Space over a Field]]
- [[Reducibility of Linear Transformation]]


## Decomposition of Linear Map

>[!important] Theorem
>Every *linear map* $A \in L(V)$ on a *finite-dimensional space* $V$ is the **direct sum** of a **nilpotent transformation** and an **invertible transformation**.

- [[Surjective Injective Invertible Linear Map and Rank]]


## Krylov Subspace

- [[Krylov Subspace]]



-----------
##  Recommended Notes and References

- [[Matrix]]

- [[Reducibility of Linear Transformation]]
- [[Invariance under Linear Transformation]]
- [[Linear Subspace]]
- [[Direct Sum of Subspaces]]
- [[Linear Independence]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]] pp 109 - 111