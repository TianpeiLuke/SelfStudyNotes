---
tags:
  - concept
  - math/convex_analysis
keywords:
  - affine_combination
topics:
  - convex_analysis
name: Affine Combination
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Affine Combination

>[!important] Definition
>Let $a_{1} \,{,}\ldots{,}\, a_{n}$ be points in a *vector space* over $F$ or *affine space*, and $\lambda_{1} \,{,}\ldots{,}\, \lambda_{n}$ are scalars in $F$ such that 
>$$
>\sum_{i=1}^n\lambda_{i}  = 1.
>$$
>
>Then the **affine combination** of  $a_{1} \,{,}\ldots{,}\, a_{n}$  is denoted as
>$$
>\sum_{i=1}^n \lambda_{i} a_{i}
>$$

- [[Affine Space]]

## Explanation

>[!info]
>For any point $o \in A$ in the affine space $A$, the affine combination of $a_{i}\in A$ can be seen as **linear combination of translations** with respect to origin $o$.
>
>That is, there exists a unique point $g\in A$ such that 
>$$
>(g-o) =  \sum_{i=1}^n\lambda_{i} (a_{i} - o) = \left(\sum_{i=1}^n \lambda_{i} a_{i}\right) - o
>$$
>given that 
>$$
>\sum_{i=1}^n\lambda_{i}  = 1.
>$$
>
>The definition of affine combination is **independent to the choice of origin**.



-----------
##  Recommended Notes and References


- [[Linear Combination]]
- [[Affine Space]]

- [[Convex Analysis by Rockafellar]]
- [[Matrix Analysis by Horn]]

- Wikipedia [Affine space](https://en.wikipedia.org/wiki/Affine_space)
- Wikipedia [Affine combination](https://en.wikipedia.org/wiki/Affine_combination)