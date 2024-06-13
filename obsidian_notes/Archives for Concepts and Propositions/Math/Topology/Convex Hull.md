---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_hull
topics:
  - convex_analysis
name: Convex Hull
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Convex Hull

>[!important] Definition
>The **convex hull** of a set $X$, denoted as $\text{conv}(X)$,  is the *smallest convex set* containing $X$. That is,
>$$
>\text{conv}(X) = \bigcap \left\{ C:  C \text{ is convex and } C \supseteq X \right\}
>$$


## Explanation


>[!important] Proposition
>For any subset $X \subset \mathbb{R}^n$, 
>$$
>\text{conv}(X) = \left\{ \sum_{i=1}^{m}\lambda_{i}x_{i}:  \exists m \in \mathbb{N}, x_{i} \in X, \lambda_{i} \ge 0, \sum_{i=1}^{m}\lambda_{i} = 1. \right\}
>$$


 >[!info]
 >By [[Carathéodory Theorem for Convex Hull]], we know that $m \leq n+1$.




-----------
##  Recommended Notes and References

- [[Convex Set]]
- [[Convex Combination]]

- [[Convex Analysis by Rockafellar]]