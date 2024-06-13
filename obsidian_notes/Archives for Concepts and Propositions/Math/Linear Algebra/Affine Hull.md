---
tags:
  - concept
  - math/convex_analysis
keywords:
  - affine_hull
topics:
  - convex_analysis
name: Affine Hull
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Convex Hull

>[!important] Definition
>The **affine hull** of a set $X$, denoted as $\text{aff}(X)$,  is the *smallest affine space* containing $X$. That is,
>$$
>\text{aff}(X) = \bigcap \left\{ A:  A \text{ is affine space and } A \supseteq X \right\}
>$$

- [[Convex Hull]]
## Explanation


>[!important] Proposition
>For any subset $X \subset \mathbb{R}^n$, 
>$$
>\text{aff}(X) = \left\{ \sum_{i=1}^{m}\lambda_{i}x_{i}:  \exists m \in \mathbb{N}, x_{i} \in X,  \sum_{i=1}^{m}\lambda_{i} = 1. \right\}
>$$


 >[!info]
 >By definition of [[Convex Hull]], 
 >$$
 >\text{conv}(X) \subset \text{aff}(X).
 >$$




-----------
##  Recommended Notes and References

- [[Convex Set]]
- [[Convex Combination]]

- [[Convex Analysis by Rockafellar]]