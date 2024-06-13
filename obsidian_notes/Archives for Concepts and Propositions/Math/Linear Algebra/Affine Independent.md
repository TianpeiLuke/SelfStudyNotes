---
tags:
  - concept
  - math/convex_analysis
keywords:
  - affine_independent
topics:
  - convex_analysis
name: Affine Independent
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Affine Independent

>[!important] Definition
>For an affine space $A$, together with a vector space $V$ over field $F$, a set of points $\{x_{0} \,{,}\ldots{,}\, x_{n} \}$ in $A$   is **affinely independent**, if the collection of subtractions
>$$
>\{x_{1} - x_{0} \,{,}\ldots{,}\, x_{n} - x_{0} \}
>$$
>are *linearly independent* in $V$

- [[Affine Space]]
- [[Linear Independence]]


>[!important] Alternative Definition
>For an affine space $A$, together with a vector space $V$ over field $F$, a set of points $\{x_{0} \,{,}\ldots{,}\, x_{n} \}$ in $A$   is **affinely independent**, if
>$$
>\sum_{i=0}^n \lambda_{i} x_{i} = 0, \text{ and } \sum_{i=0}^n \lambda_{i} = 0
>$$
>*only if* $\lambda_{i} = 0$ for $i=0 \,{,}\ldots{,}\,n.$





## Explanation

>[!important] Proposition
>A set of $n+1$ points $X := \{x_{0} \,{,}\ldots{,}\, x_{n} \}$ in $A$ is **affinely independent**, if 
>$$
>\text{dim}(\text{aff}(X)) = n.
>$$

- [[Affine Hull]]

>[!important] Proposition
>A set of $n$ points $X := \{x_{1} \,{,}\ldots{,}\, x_{n} \}$ in $A \subset \mathbb{R}^n$ is **affinely independent**, if the vectors 
>$$
>(1, x_{1}) \,{,}\ldots{,}\,(1, x_{n}), \quad (0, x_{1}) \,{,}\ldots{,}\,(0, x_{n})
>$$
>are linearly independent in $\mathbb{R}^{n+1}$.






-----------
##  Recommended Notes and References


- [[Linear Independence]]
- [[Affine Combination]]
- [[Affine Space]]

- [[Convex Analysis by Rockafellar]]
- [[Matrix Analysis by Horn]]

- Wikipedia [Affine space](https://en.wikipedia.org/wiki/Affine_space)