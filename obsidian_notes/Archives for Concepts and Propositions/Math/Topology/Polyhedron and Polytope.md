---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - machine_learning/theory
keywords:
  - polyhedral_set
  - polytope_set
topics:
  - convex_analysis
  - optimization/theory
  - machine_learning_theory
name: Polyhedral and Polytope
date of note: 2024-07-22
---

## Concept Definition

>[!important]
>**Name**: Polyhedron and Polytope

>[!important] Defintion
>A set $P$ is called a **(convex) polyhedron** if it can be represented as the *intersection* of a *finite number* of *half-spaces*.
>$$
>P = \bigcap_{i=1}^{n}H_{i}
>$$
>where $H_{i} \supseteq P.$
>
>If $P \subset \mathbb{R}^{d}$, it can be represented as
>$$
>P = \left\{ x\in \mathbb{R}^{d}: \left\langle a_{j} , x \right\rangle \le b_{j},\quad \forall j\in J\right\}
>$$
>where for each $j\in J$, the pair $(a_{j}, b_{j})\in \mathbb{R}^{d+1}$ parameterizes a particular *half-space*.

>[!important] Definition
>A *bounded* polyhedron is called a **polytope**.

>[!info]
>Plura term **polyhedra.**

## Explanation

![[Support functional of Convex Set#^ab1379]]

>[!info]
>A polyhedron is a *convex set*.

- [[Convex Set]]

## Extreme Points

- [[Extreme Points of Convex Set of Locally Convex Space]]
- [[Krein-Milman Lemma and Krein-Milman Theorem]]

![[Krein-Milman Lemma and Krein-Milman Theorem#^8e5fc2]]

>[!important] Proposition
>Any non-empty **polyhedron** $P$ can be written as the convex hull of **extreme points**. 
>
>Conversely, the convex hull of  any *finite collection of vectors* is a **polytope**.

- [[Generalized Simplex]]


-----------
##  Recommended Notes and References

- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]
	- [[Supporting Hyperplane of Convex Set]]
	- [[Separation Theorem]]

- [[Supporting Hyperplane of Convex Set]]
- [[Support functional of Convex Set]]


- [[Generalized Simplex]]
- [[Simplex Method for Linear Optimization]]
- [[Interior Point Method for Linear Optimization]]


- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]
- [[Convex Optimization Algorithms by Bertsekas]]
- [[Introduction to Linear Optimization by Bertsimas]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 263

- Wikipedia [Polyhedron](https://en.wikipedia.org/wiki/Polyhedron)
- Wikipedia [Polytope](https://en.wikipedia.org/wiki/Polytope)