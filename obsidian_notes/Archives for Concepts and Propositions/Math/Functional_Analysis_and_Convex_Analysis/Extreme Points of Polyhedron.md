---
tags:
  - concept
  - math/functional_analysis
  - optimization/theory
  - math/topology
keywords:
  - extreme_points
  - convex_set
  - locally_convex_space
topics:
  - functional_analysis
  - topology
  - geometry
name: Extreme Points of Polyhedron
date of note: 2024-06-21
---

## Concept Definition

>[!important]
>**Name**: Extreme Points of Polyhedron

![[Extreme Points of Convex Set of Locally Convex Space#^36426c]]

>[!important] Definition
>Let $P$ be a *polyhedron*. 
>
>A vector $x\in P$ is an **ex­treme point** of $P$ if we *cannot find* two vectors $y, z \in P$, both *different from* $x$, and a scalar $\lambda\in [0,1]$ such that $$x = \lambda\,y + (1- \lambda)\,z.$$
>
>That is, $x\in P$ is an **extreme point** if and only if
> $$(\exists \lambda \in [0,1])\;\; x = \lambda u + (1- \lambda)v\; \implies u = v = x.$$

^3396c2

- [[Vertex Point of Polyhedron]]
- [[Introduction to Linear Optimization by Bertsimas]] pp 46
- [[Extreme Points of Convex Set of Locally Convex Space]]


## Explanation



## Krein-Milman Theorem and Characterization of Extreme Points

>[!important] Proposition
>Any non-empty **polyhedron** $P$ can be written as the convex hull of **extreme points**. 
>
>Conversely, the convex hull of  any *finite collection of vectors* is a **polytope**.


- [[Krein-Milman Lemma and Krein-Milman Theorem]]




-----------
##  Recommended Notes and References

- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Locally Convex Space]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]

- [[Real Analysis by Royden]] pp 295 - pp 296
- [[Partial Differential Equations by Evans]]