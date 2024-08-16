---
tags:
  - concept
  - math/functional_analysis
keywords:
  - extreme_points
  - convex_set
  - locally_convex_space
topics:
  - functional_analysis
name: Extreme Points of Convex Set of Locally Convex Space
date of note: 2024-06-21
---

## Concept Definition

>[!important]
>**Name**: Extreme Points of Convex Set of Locally Convex Space

>[!important] Definition
>Let $K$ be a non-empty *convex* subset of a *locally convex topological vector space* $\mathcal{X}.$
>
>A non-empty subset $E$ of $K$ is called an **extreme subset** of $K$ if
>- it is both **convex** and **closed**, 
>- and whenever $x \in E$ is a **convex combination** of vectors $u$ and $v$ in $K$, then both $u$ and $v$ belongs to $E$, i.e. $$(\exists x \in E)\;(\exists \alpha\in [0,1])\;\; x = \alpha u + (1- \alpha)v\; \implies u, v \in E.$$
>
>A point $x \in K$ is called an **extreme point** of $K$ if the singleton set $\{ x \}$ is an *extreme subset* of $K$.

^36426c

- [[Vertex Point of Polyhedron]]
- [[Basic Solution for Linear Optimization]]

### Extreme Point for Polyhedron

![[Extreme Points of Polyhedron#^3396c2]]

- [[Extreme Points of Polyhedron]]
- [[Vertex Point of Polyhedron]]
- [[Introduction to Linear Optimization by Bertsimas]] pp 46


## Explanation



## Krein-Milman Theorem and Characterization of Extreme Points

- [[Krein-Milman Lemma and Krein-Milman Theorem]]




-----------
##  Recommended Notes and References

- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Locally Convex Space]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]

- [[Real Analysis by Royden]] pp 295 - pp 296
- [[Partial Differential Equations by Evans]]