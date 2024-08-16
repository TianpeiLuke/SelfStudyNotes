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

### Active Constraint for LP

![[Active and Independent Constraints for Linear Optimization#^90a3c5]]

- [[Active and Independent Constraints for Linear Optimization]]

### Basic Solution for LP

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

>[!important] Corollary
>Given a **finite** number of **linear inequality constraints**, there can only be a **finite** number of **basic or basic feasible solutions**.

### Adjacent Basic Solution

>[!important] Definition
>Two distinct basic solutions to a set of *linear constraints* in $\mathbb{R}^{n}$ are said to be **adjacent** if we can find $n - 1$ *linearly independent constraints* that are *active* at both of them.



## Explanation

>[!info]
>Note that if the number $m$ of **constraints** used to define a polyhedron $P \subset \mathbb{R}^{n}$ is *less than* $n$, $$m\le n$$ the **number of active constraints** at any given point must also be *less than* $n$, and there are **no basic** or **basic feasible solutions**.


## Polyhedral in standard form

>[!important]
>Let $$P = \left\{ x\in \mathbb{R}^{n}:\; Ax = b,\; x \succeq 0 \right\} $$ be a polyhedron in **standard form**, and let $A \in \mathbb{R}^{m\times e n}$, where $m$ is the number of **equality constraints**.

- [[Linear Optimization Problem]]
- [[Introduction to Linear Optimization by Bertsimas]] pp 53

>[!important] Theorem
>Consider the constraints $Ax = b$, and $x \succeq 0$ and assume that the $m \times n$ matrix $A$ has **linearly independent rows**. 
>
>A vector $x\in \mathbb{R}^{n}$ is a **basic solution** *if and only if* we have $Ax = b$, and there exist **indices** $$B(1) \,{,}\ldots{,}\, B(m)$$ such that:
>- The columns $$A_{B(1)} \,{,}\ldots{,}\,A_{B(m)}$$ are **linearly independent**;
>- If $i \neq B(1) \,{,}\ldots{,}\, B(m)$, then $$x_{i} = 0$$

- [[Active and Independent Constraints for Linear Optimization]]


## Procedure for Constructing Basic Solution

>[!important] Procedure for constructing basic solutions
>1. Choose $m$ **linearly independent columns** $$A_{B(1)} \,{,}\ldots{,}\,A_{B(m)}·$$ 
>2. Let $x_{i} = 0$ for all $i \neq B(1) \,{,}\ldots{,}\, B(m)$. 
>3. Solve the **system of $m$ equations** $$Ax = b$$ for the unknowns $$x_{B(1)} \,{,}\ldots{,}\,x_{B(m)}$$





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