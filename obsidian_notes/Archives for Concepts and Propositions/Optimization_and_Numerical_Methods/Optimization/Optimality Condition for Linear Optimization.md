---
tags:
  - concept
  - optimization/theory
keywords:
  - extreme_points
  - polyhedral_set
  - linear_optimization
  - optimal_solution
topics:
  - optimization/theory
name: Optimality Condition for Linear Optimization
date of note: 2024-08-17
---

## Concept Definition

>[!important]
>**Name**: Optimality Condition for Linear Optimization

![[Feasible Direction and Reduced Cost for Linear Optimization#^670d89]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^6f654f]]


>[!important] Theorem
>Consider a **basic feasible solution** $x$ associated with a **basis matrix** $B$, and let $\bar{c}$ be the corresponding vector of **reduced costs.**
>
>- If $\bar{c} \ge 0$, then $x$ is **optimal.** 
>- If $x$ is **optimal** and **non-degenerate**, then $\bar{c} \ge 0$.

^521cec

- [[Feasible Direction and Reduced Cost for Linear Optimization]]
- [[Basic Solution for Linear Optimization]]
- [[Degeneracy of Basic Solution in Linear Optimization]]
- [[Linear Optimization Problem]]
- [[Optimality of Extreme Point in Linear Optimization]]


>[!important] Definition
>A basis matrix $B$ is said to be **optimal** if
>- the *basic feasible solution* $$B^{-1}b \succeq 0$$
>- the *reduced cost* $$\bar{c} = c - \,A^{T}\,B^{-1}\,c_{B} \succeq 0$$






## Explanation




-----------
##  Recommended Notes and References


- [[Existence of Extreme Point in Polyhedron]]
- [[Extreme Points of Polyhedron]]
- [[Polyhedron and Polytope]]
- [[Linear Optimization Problem]]
- [[Generalized Simplex]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]


- [[Linear Independence]]
- [[Matrix]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 65