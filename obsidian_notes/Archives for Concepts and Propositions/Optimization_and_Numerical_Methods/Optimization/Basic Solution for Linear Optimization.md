---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - linear_optimization
  - basis_vector_space
  - basic_solution_linear_optimization
topics:
  - optimization/algorithm
name: Basic Solution for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Basic Solution for Linear Optimization

![[Linear Optimization Problem#^099c2f]]

![[Constrained Optimization Problem#^9a3b41]]

>[!important] Definition
>If a vector $x^{*}$ satisfies the *equality condition* for the corresponding *inequality or inequality constraint*, then we say that the corresponding constraint is **active** or **binding** at $x^{*}$.


>[!important] Definition
>Consider a *polyhedron* $P$ defined by linear equality and inequality constraints, and let $x^{*}\in \mathbb{R}^{n}$.
>
>A vector $x^{*}\in \mathbb{R}^{n}$ is said to be a **basic solution** of LP if
>- All *equality constraints* are *active*;
>- Out of  constraints that are *active* at $x^{*}$, there are $n$ of them that are *linearly independent*.

^52390c

- [[Constrained Optimization Problem#Active and Inactive Constraints]]
- [[Polyhedron and Polytope]]
- [[Linear Independence]]

>[!important] Definition
>If $x^{*}$ is a *basic solution* that satisfies *all of the constraints*, we say that it is a **basic feasible solutions**.

### Basic Feasible Solution and Extreme Point

![[Vertex Point of Polyhedron#^0265a0]]

![[Extreme Points of Polyhedron#^3396c2]]


>[!important] Theorem
>Let $P$ be a nonempty polyhedron and let $x^{*} \subset P$. Then, the following are **equivalent**:
>- $x^{*}$ is a **vertex**;
>- $x^{*}$ is an **extreme point**;
>- $x^{*}$ is a **basic feasible solution**.


- [[Vertex Point of Polyhedron]]
- [[Polyhedron and Polytope]]
- [[Extreme Points of Polyhedron]]
- [[Krein-Milman Lemma and Krein-Milman Theorem]]


## Explanation

>[!info]
>Note that if the number $m$ of **constraints** used to define a polyhedron $P \subset \mathbb{R}^{n}$ is *less than* $n$, $$m\le n$$ the **number of active constraints** at any given point must also be *less than* $n$, and there are **no basic** or **basic feasible solutions**.







-----------
##  Recommended Notes and References


- [[Optimality Condition and Feasible Direction for Linear Optimization]]
- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Simplex Method for Linear Optimization]]
- [[Constrained Optimization Problem]]


- [[Introduction to Linear Optimization by Bertsimas]] pp 50, 52
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Introduction to Algorithms by Cormen]]