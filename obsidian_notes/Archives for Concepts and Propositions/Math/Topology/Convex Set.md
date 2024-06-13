---
tags:
  - concept
  - math/topology
  - optimization/theory
  - math/functional_analysis
  - math/convex_analysis
keywords:
  - convex_set
topics:
  - topology
  - convex_analysis
name: Convex Set
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Convex Set


>[!important] Definition
>A set $A$ in a *vector space* $X$ is called **convex**, if for any $x, y \in A$, and $0 \leq t \leq 1$, we have
>$$
>tx + (1-t)y \in A.
>$$

>[!important] Definition
>Given an **ordered set** $X$, let us say that a subset $Y$ of $X$ is **convex** in $X$ if for *each pair* of points $a < b$ of $Y$,  *the entire interval* $(a, b)$ of points of $X$ *lies in* $Y$. 

- [[Well Ordered Set]]

>[!info]
>Note that **intervals** and **rays** in $X$ are **convex** in $X$.



## Explanation

>[!info]
>Let $a_{1} \,{,}\ldots{,}\, a_{n}$ be points in a *convex  set* $C$, then **the convex combination** of these points also lies in $C$, by definition of convexity
>$$
>\sum_{i=1}^n \lambda_{i} a_{i} \in C
>$$
>
>**Conversly,** a set $C$ is convex, if it contains *all convex combination of its points.*
>$$
>C = \left\{ \sum_{i=1}^n \lambda_{i} a_{i}: \forall a_{i} \in C, \lambda_{i} \ge 0, \sum_{i=1}^n \lambda_{i} = 1 \right\}
>$$

- [[Convex Combination]]

## Properties

>[!important] Proposition
>The **intersection** of *arbitrary collection* of *convex sets* is **convex**.
>$$
> \left\{ C_{i}: C_{i} \text{ convex},  i\in I \right\}   \implies \bigcap_{i\in I}C_{i} \text{ convex}
>$$



## Dimensionality

>[!important] Definition
>The **dimensionality** of a convex set $C$, denoted, $\text{dim}(C)$ is the dimensionality of *the affine hull* of it.
>$$
>\text{dim}(C) = \text{dim}(\text{aff}(C))
>$$

- [[Affine Hull]]
- [[Affine Space]]


-----------
##  Recommended Notes and References

- [[Affine Space]]
- [[Convex Combination]]

- [[Topological Vector Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)


- [[Convex Analysis by Rockafellar]]
- [[Topology Book by Munkres]]