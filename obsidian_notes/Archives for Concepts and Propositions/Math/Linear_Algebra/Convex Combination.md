---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_combination
topics:
  - convex_analysis
name: Convex Combination
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Convex Combination

>[!important] Definition
>Let $a_{1} \,{,}\ldots{,}\, a_{n}$ be points in a *vector space*, and $\lambda_{1} \,{,}\ldots{,}\, \lambda_{n}$ are  scalars satisfying
>- **non-negativity**:
>  $$\lambda_{i} \ge 0, i=1 \,{,}\ldots{,}\, n.$$
>- **normalization**:
> $$
>\sum_{i=1}^n\lambda_{i}  = 1.
>$$
> 
>
>Then the **convex combination** is denoted as
>$$
>\sum_{i=1}^n \lambda_{i} a_{i}
>$$

- [[Linear Combination]]
- [[Affine Combination]]


## Explanation

>[!info]
>Convex combination applies to [[Affine Space]] as well. 

>[!info]
>Convex combination is [[Affine Combination]] with additional **non-negativity constraints**.

>[!info]
>Let $a_{1} \,{,}\ldots{,}\, a_{n}$ be points in a *convex  set* $C$, then the convex combination of these points also lies in $C$, by definition of convexity
>$$
>\sum_{i=1}^n \lambda_{i} a_{i} \in C
>$$
>
>**Conversly,** a set $C$ is convex, if it contains *all convex combination of its points.*
>$$
>C = \left\{ \sum_{i=1}^n \lambda_{i} a_{i}: \forall a_{i} \in C, \lambda_{i} \ge 0, \sum_{i=1}^n \lambda_{i} = 1 \right\}
>$$




-----------
##  Recommended Notes and References

- [[Convex Set]]


- [[Convex Analysis by Rockafellar]]
- Wikipedia [Convex combination](https://en.wikipedia.org/wiki/Convex_combination)
