---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - simplex_method_linear
  - linear_optimization
topics:
  - optimization/algorithm
name: Optimality Condition and Feasible Direction for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Optimality Condition and Feasible Direction for Linear Optimization

![[Linear Optimization Problem#^099c2f]]

### Feasible Direction

>[!important] Definition
>Let $x$ be an element of a *polyhedron* $P$. 
>
>A vector $d\in \mathbb{R}^{n}$ is said to be a **feasible direction** at $x$, if there exists a *positive* scalar $\theta$ for which $$x + \theta\,d \in P.$$

- [[Polyhedron and Polytope]]

### Basic Solution 

![[Basic Solution for Linear Optimization#^52390c]]

- [[Basic Solution for Linear Optimization]]
- [[Extreme Points of Polyhedron]]
- [[Vertex Point of Polyhedron]]
- [[Active and Independent Constraints for Linear Optimization]]


## Explanation



>[!quote]
>Many optimization algorithms are structured as follows: given a *feasible solution*, we *search its neighborhood* to find a nearby feasible solution with *lower cost*. If no nearby feasible solution leads to a cost improvement , the algorithm *terminates* and we have a **locally optimal solution**. For general optimization problems, a locally optimal solution need not be (globally) optimal. Fortunately, in linear programming, **local optimality implies global optimality**; this is because we are minimizing a convex function over a convex set.
>
>-- [[Introduction to Linear Optimization by Bertsimas]] PP 82




-----------
##  Recommended Notes and References


- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Interior Point Method for Linear Optimization]]
- [[Simplex Method for Linear Optimization]]

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 81
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Introduction to Algorithms by Cormen]]