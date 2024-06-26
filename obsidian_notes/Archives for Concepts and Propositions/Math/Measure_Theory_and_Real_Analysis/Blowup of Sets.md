---
tags:
  - concept
  - math/topology
  - statistics/concentration_inequality
  - math/measure_theory
keywords:
  - blowup_set
topics:
  - topology
  - measure_theory
  - concentration_inequality
name: Blowup of Sets
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Blowup of Sets


>[!important] Definition
>For any $t > 0$, and any *(measurable) sets* $A \subset \mathbb{R}^n$,  **the $t$-blowup** (or, **$t$-enlargement** of $A$) is defined by
>$$
> \begin{align*}
> A_t &:= \set{x \in \mathbb{R}^n: d(x, A) < t} = A + t\,B
> \end{align*}
>$$  
>where $B = \set{x \in \mathbb{R}^n: d(0, x) < 1}$ is an *open unit ball* and $$d(x, A) = \inf_{y \in A}d(x, y).$$

- [[Minkowski Sum of Sets]]
- [[Metric Space]]


## Explanation





-----------
##  Recommended Notes and References

- [[Minkowski Sum of Sets]]
- [[Metric Space]]


- [[Concentration Inequalities by Boucheron]]