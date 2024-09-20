---
tags:
  - concept
  - math/linear_algebra
keywords:
  - rank_nulllity_theorem
topics:
  - linear_algebra
name: Rank–Nullity theorem
date of note: 2024-05-27
---

## Theorem

>[!important]
>**Name**: Rank–Nullity Theorem

>[!important]  Rank–Nullity Theorem
>Let $V$  be finite dimensional vector spaces and $W$ be a vector space and $A: V \to W$ be a linear transformation.
>
>Then the **dimension of domain** $V$ can be computed as
>$$
>\text{dim}(V) = \text{rank}(A) + \text{nullity}(A)
>$$
>where $\text{rank}(A)$ is the **rank** of $A$ and $\text{nullity}(A)$ is the **nullity** of $A$.

- [[Linear Map]]
- [[Rank and Nullity of Linear Map]]


## Explanation

>[!info]
>In other word,
>$$
>\text{dim}\;\text{domain}(A) = \text{dim}\;\text{Im}(A) + \text{dim}\;\text{Ker}(A)
>$$

![[Fundamental Subspaces from Linear Map and its Projection#^3f989c]]

- [[Fundamental Subspaces from Linear Map and its Projection]]

## Quotient of Domain Modulo Kernel


>[!important]
>By above theorem, we see that $A$ induces an **isomorphism** between the *quotient space* $V / \text{ker}(A)$ and $\text{Im}(A)$
>$$
>V / \text{ker}(A) \simeq \text{Im}(A)
>$$

- [[Quotient Space of Vector Space]]
- [[Linear Isomorphism]]




-----------
##  Recommended Notes and References


- [[Rank and Nullity of Linear Map]]
- [[Range and Kernel of Linear Map]]

- [[Linear Map]]
- [[Vector Space over a Field]]