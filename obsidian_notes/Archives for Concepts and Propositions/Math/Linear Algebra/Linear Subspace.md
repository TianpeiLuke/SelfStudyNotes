---
tags:
  - concept
  - math/linear_algebra
keywords:
  - linear_subspace
topics:
  - linear_algebra
name: Linear Subspace
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Linear Subspace

>[!important] Definition
>A non-empty subset $S$ of a vector space $V$ is a **subspace** or a **linear manifold** if along with every pair, $x$ and $y$, of vectors contained in $S$, *every linear combination* of $\alpha x + \beta y$ is also contained in $S$.
>
>$$
>\forall x, y \in S \implies \alpha x + \beta y \in S, \quad \forall \alpha, \beta \in F
>$$

>[!info]
>A *subspace* of a vector space is **closed** under *vector addition* and *scalar multiplication* operations.

>[!important] Equivalent Definition
>Let $V$ be a vector space over $F$. A subset $S \subset V$ is a **subspace** if $S$ is a *vector space* over $F$ under vector addition and scalar multiplication over $V$. 

## Explanation


## Properties:


>[!important] Theorem
>Let $V$ be a $n$-dimensional vector space. $S \subset V$ is a subspace, then $\text{dim }S \le n$. 

>[!important] Proposition
>Let $V$ be a $n$-dimensional vector space. $S \subset V$ is a *subspace*, then $S$ is **closed** under $V$

>[!important] Proposition
>The **intersection** of *any* collection of *subspaces* is a *subspace*.


>[!important] Proposition
>Let $U$ and $W$ be *subspaces* of $V$. Then the **sum** of $U$ and $W$, defined by
>$$
>U + W := \{ u + w: u\in U, w\in W \}
>$$
>is also a **subspace** of $V$.
>
>In particular, the **dimension of the sum** of $U$ and $W$ is
>$$
>\text{dim}(U + W) = \text{dim}(U) + \text{dim}(W) - \text{dim}(U \cap W)
>$$








-----------
##  Recommended Notes and References

- [[Linear Span over a Set of Vectors]]
- [[Vector Space over a Field]]
- [[Smooth Manifold]]
- [[Finite Dimensional Vector Spaces by Halmos]]

- Wikipedia [Linear subspace](https://en.wikipedia.org/wiki/Linear_subspace)