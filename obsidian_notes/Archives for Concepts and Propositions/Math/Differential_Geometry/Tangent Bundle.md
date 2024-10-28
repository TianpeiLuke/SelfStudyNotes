---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_bundle
topics:
  - differential_geometry
name: Tangent Bundle
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Tangent Bundle $TM$

>[!important] Definition 
>Given a *smooth manifold* $M$ with or without boundary, the **tangent bundle** of $M$, denoted by $TM$, is defined as the **disjoint union** of *the tangent spaces* **at all points** of $M$:
>$$
> \begin{align*}
> TM &= \bigsqcup_{p \in M}T_{p}M.
> \end{align*}
>$$ 

- [[Tangent Space Definition and Development]]
- [[Vector Space over a Field]]

>[!important] Definition
>We usually write an *element* of this *disjoint union* as **an ordered pair** $(p, v)$, with $p \in M$ and $v \in T_{p}M$.

>[!info]
>This representation is called **phase space** in physics, where $p$ is the *position* of particle, and $v$ is the *velocity (momentum)*. 
>
>So think of a **tangent bundle** is a *physical system of particles* moving on a surface $M$.
>
>The *natural projection map* associates the *velocity* of particle to the *position* of the particle.

>[!important] Definition
>The tangent bundle comes equipped with a **natural projection map** $\pi: TM \rightarrow M$, which sends *each vector* in $T_{p}M$ to the *point* $p$ at which it is tangent: $$\pi(p, v) = p.$$

- [[Canonical Projection]]

>[!info]
>We will often commit the usual mild sin of identifying $T_{p}M$ with its image under the canonical injection $v \mapsto (p, v)$, and will use any of the notations **$(v, p),  v_{p}$ and $v$** for a *tangent vector* in $T_{p}M$, depending on how much emphasis we wish to give to the point $p$.


## Explanation

>[!important]
>The definition of tangent bundle reflects a key perspective in differential geometry:
>
>We are seeking math objects that are **invariant** *under* the **change of coordinate system**. In this setup, each coordinate system is attached to a tangent space at a specific point in the manifold.
>
>**The tangent bundle** is a *domain* that *collects all  tangent spaces* and their coordinate systems.

>[!info]
>*Tangent bundle* provides a *pairing* between the **nonlinear smooth manifold** $M$ and **its local linear approximations** $T_{p}M$ at $p\in M$.

>[!info]
>Tangent bundle is **the default domain** for many *functions on tangent vectors*.

![[coordinate_tangent_bundle.png]]

### Tangent Space as Space of Free Vectors


>[!info]
>Consider an **affine space** $M$, then $T_{p}M$ at every $p\in M$ are all *parallel* to each other. This vector space $T_{p}M$ is **the vector space of free vectors** that is associated with **affine space** $M$.
>
>This means that for general smooth manifold, the tangent bundle $TM$ serve the role of **the vector space of free vectors**.

- [[Affine Space]]
- [[Parallel Subspaces]]

## Properties

>[!info]
>The tangent bundle is also a smooth manifold with $(p, v)$, thus has dimensionality $2n$.

>[!important] Proposition
>For any *smooth* $n$-manifold $M$, the **tangent bundle** $TM$ has a **natural topology** and **smooth structure** that make it into a **$2n$-dimensional smooth manifold**. 
>
>With respect to this structure, the *projection* $\pi: TM \rightarrow M$ is **smooth**.

>[!info]
>Interestingly, this suggests that the **derivative** $v$ at $p$ is **linearly independent** from **the position** vector $p$ .






-----------
##  Recommended Notes and References



- [[Vector Bundle]]