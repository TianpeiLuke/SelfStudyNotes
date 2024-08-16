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
name: Active and Independent Constraints for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Active and Independent Constraints for Linear Optimization

![[Linear Optimization Problem#^099c2f]]

![[Constrained Optimization Problem#^9a3b41]]

### Active Constraint for LP

>[!important] Definition
>If a vector $x^{*}$ satisfies the *equality condition* for the corresponding *inequality or inequality constraint*, then we say that the corresponding constraint is **active** or **binding** at $x^{*}$.

^90a3c5


>[!important] Proposition
>Let $x^{*}$ be an element in $\mathbb{R}^{n}$ and let $$I = \left\{ i: \left\langle  a_{i}\,,\, x^{*}   \right\rangle = b_{i} \right\} $$ be the set of *indices* of *constraints* that are **active** at $x^{*}$. Then, the following are **equivalent**:
>- There exists $n$ vectors in the set $$\left\{ a_{i}: i\in I \right\},$$ which are **linearly independent**.
>- The **span** of the vectors $\left\{ a_{i}: i\in I \right\}$, is **all** of $\mathbb{R}^{n}$, that is, every element of $\mathbb{R}^{n}$ can be expressed as a **linear combination** of the vectors $a_{i}, i\in I$.
>- The system of *equations* $$\left\langle  a_{i}\,,\, x^{*}   \right\rangle = b_{i}, \;\; i\in I$$ has a **unique solution**.

>[!important] Definition
>With a slight abuse of language, we will often say that certain **con­straints** are **linearly independent**, meaning that the corresponding vectors $a_{i}$ are *linearly independent*.

- [[Linear Independence]]


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