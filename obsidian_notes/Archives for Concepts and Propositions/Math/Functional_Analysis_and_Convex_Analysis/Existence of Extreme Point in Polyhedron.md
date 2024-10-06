---
tags:
  - concept
  - optimization/theory
  - optimization/linear_optimization
keywords:
  - extreme_points
  - polyhedral_set
topics:
  - optimization/theory
name: Existence of Extreme Point in Polyhedron
date of note: 2024-08-17
---

## Concept Definition

>[!important]
>**Name**: Existence of Extreme Point in Polyhedron

>[!important] Definition
>A *polyhedron* $P \subset \mathbb{R}^{n}$ **contains a line** if there exists a vector $x \in P$ and a *nonzero vector* $d \in \mathbb{R}^{n}$ such that $$x + \lambda\, d \in P, \quad \forall \lambda \in \mathbb{R},$$

- [[Convex Set]]
- [[Polyhedron and Polytope]]

>[!important] Theorem
>Suppose that the **polyhedron** $$P = \left\{ x\in \mathbb{R}^{n}: \; \left\langle  a_{i}\,,\, x \right\rangle \ge b_{i}, \quad i=1 \,{,}\ldots{,}\,m \right\}$$ is non-empty.
>
>Then the following are **equivalent**:
>- The polyhedron $P$ has **at least one extreme point**.
>- The polyhedron $P$ does **not contains a line**.
>- There exists $n$ vectors out of the family $\{ a_{i}, i=1\,{,}\ldots{,}\,m \}$ which are **linearly independent.**

^5b9aa0

- [[Extreme Points of Polyhedron]]
- [[Linear Independence]]
- [[Active and Independent Constraints for Linear Optimization]]

>[!important] Corollary
>Every non-empty **bounded polyhedron** and every non-empty polyhedron in standard form has *at least one* **basic feasible solution**.

^c2ffc7

- [[Basic Solution for Linear Optimization]]


## Explanation


## Krein-Milman Lemma

![[Krein-Milman Lemma and Krein-Milman Theorem#^5eae27]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]



-----------
##  Recommended Notes and References


- [[Extreme Points of Polyhedron]]
- [[Polyhedron and Polytope]]
- [[Linear Optimization Problem]]
- [[Generalized Simplex]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]


- [[Linear Independence]]
- [[Matrix]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 62 - 64