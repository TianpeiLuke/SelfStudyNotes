---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - spanned_vector_space
topics:
  - linear_algebra
  - functional_analysis
name: Linear Span over a Set of Vectors
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Linear Span over a Set of Vectors

>[!important] Definition
>Given a *vector space* $V$ over a field $F$, the **span** of a set $S$ of *vectors* (*not necessarily finite*) is defined to be the *intersection* $W$ of all *subspaces* of $V$ that *contain* $S$. 
>
>$$
>\text{span}(S) = \bigcap \{W: W \supset S, \;\; W \text{ is a subspace of }V  \}
>$$
>
>$W$ is referred to as the **subspace spanned by** $S$, or by the vectors in $S$.
>
 Conversely, $S$ is called a **spanning set** of $W$, and we say that $S$ **spans** $W$.



>[!important] Definition
>Given a set $S$ of vectors, the **vector space** that is **spanned** by $S$ is the set of all *finite linear combinations* of $S$. 
>
>$$
>\text{span}(S) := \left\{\sum_{i=1}^{n}\alpha_{i}x_{i}: n\in \mathbb{N}, x_{i} \in S, \alpha_{i} \in F   \right\}
>$$
>

- [[Linear Independence]]
- [[Linear Combination]]
- [[Basis of Vector Space]]


## Explanation



-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Matrix Analysis by Horn]]

- Wikipedia [Linear span](https://en.wikipedia.org/wiki/Linear_span)