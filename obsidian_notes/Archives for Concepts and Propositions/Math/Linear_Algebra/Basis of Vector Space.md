---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - basis_vector_space
topics:
  - linear_algebra
  - functional_analysis
name: Basis of Vector Space
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Basis of Vector Space

>[!important] Definition
>For a vector space $V$ over field $F$, a **(linear) basis** (or a **coordinate system**) in $V$ is a set $S$ of *linearly independent* vectors such that *every vector* in $V$ can be **uniquely** represented as a *linear combination* of elements in $S$.
>
>That is, there exists some *linearly independent subset* $S \subset V$, so that  for every $x \in V$, 
>$$
>x = \sum_{x_{i} \in S}\alpha_{i} x_{i},
>$$
>for some $(\alpha_{i})$ in $F$.

- [[Linear Independence]]
- [[Linear Combination]]


>[!important]
>A vector space $V$ is **finite-dimensional**, if it has a *finite basis*.

## Explanation

>[!info]
>Note that the bases of vector space is an **algebraic concept**, not a topological concept. This is not to be confused with [[Basis of Topology]]



-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Linear Independence]]

- [[Finite Dimensional Vector Spaces by Halmos]]