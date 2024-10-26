---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_space
topics:
  - differential_geometry
name: Tangent Space as Vector Space
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Tangent Space $T_{p}M$ as vector space

>[!important] Proposition
>If $M$ is an *$n$-dimensional smooth manifold*, then for each $p \in \mathcal{M}$ the tangent space $T_{p}\mathcal{M}$ is an **$n$-dimensional vector space.**


>[!important] Proposition
>Suppose $\mathcal{M}$ is an $n$-dimensional smooth manifold *with boundary*. 
>
>For each $p \in \mathcal{M}$, $T_{p}\mathcal{M}$ is an **$n$-dimensional vector space.**

- [[Coordinate Representation of Tangent Vector]]
- [[Vector Space over a Field]]

>[!important] Proposition
>Suppose $V$ is a finite-dimensional vector space with its standard smooth manifold structure. 
>
>For each point $a \in V$, the map $v \rightarrow D_v\big|_a$ defined by 
> $$
> \begin{align}
> D_v|_a(f) &= D_{v}(f(a)) = \frac{d}{dt}\Big|_{t=0}f(a + t\,v).
> \end{align}
> $$
> is a **canonical isomorphism** from $V$ to $T_{a}V$, such that for *any linear map* $L: V \rightarrow W$, the following diagram **commutes**:
>$$
>\begin{CD}
>
\end{CD}
>$$
> 
>![[tangent_space_to_vector_space_diagram.png]]
>

- [[Introduction to Smooth Manifolds by Lee]]


## Tangent Space as Space of Free Vectors


>[!info]
>Consider an **affine space** $M$, then $T_{p}M$ at every $p\in M$ are all *parallel* to each other. This vector space $T_{p}M$ is **the vector space of free vectors** that is associated with **affine space** $M$.
>
>This means that for general smooth manifold, the tangent bundle $TM$ serve the role of **the vector space of free vectors**.

- [[Affine Space]]
- [[Parallel Subspaces]]



-----------
##  Recommended Notes and References

- [[Tangent Space Definition and Development]]
- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Vector Space over a Field]]
