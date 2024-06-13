---
tags:
  - concept
  - math/linear_algebra
keywords:
  - projection_linear_subspace
topics:
  - linear_algebra
name: Projection on Linear Subspace
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Projection on Linear Subspace


>[!important] Definition
>If $S$ and $W$ are both linear subspaces of vector space $V$, and $V$ is the *direct sum of them*, 
>$$
>V = S \oplus W,
>$$
>so that every $z\in V$ may be written **uniquely** in the form $$z = x + y$$ for $x\in S$ and $y\in W$.
>
>The **projection** *on subspace* $S$ *along* $W$ is a map $P_{S}: V\to S$ defined by
>$$
>P_{S}\,z = x.  
>$$

- [[Invariance under Linear Transformation]]
- [[Direct Sum of Subspaces]]
- [[Linear Subspace]]


## Explanation

>[!info]
>The projection map $P_{S}$ is a **linear map**


## Properties

>[!important] Proposition
>A linear transformation $P$ is a **projection** on some subspace *if and only if* it is **idempotent**, that is, $$P^2 =P.$$

>[!important] Corollary
>If $P$ is the **projection on** $S$ **along** $W$, then $S$ and $W$ are, respectively, the sets of all solutions of the equations
>$$
>Pz = z \quad \text{ and } \quad Pz = 0.
>$$

>[!important] Proposition
>A linear transformation $P$ is a **projection**  if and only if $I- P$ is a **projection**.
>
>Furthermore, if $P$ is the *projection* **on** $S$ **along** $W$, then $I - P$ is the *projection* **on** $W$ **along** $S$.




-----------
##  Recommended Notes and References

- [[Invariance under Linear Transformation]]
- [[Linear Map]]

- [[Direct Sum of Subspaces]]
- [[Linear Subspace]]
- [[Vector Space over a Field]]


- [[Canonical Projection]]
- [[Surjective Function]]

- [[Finite Dimensional Vector Spaces by Halmos]]