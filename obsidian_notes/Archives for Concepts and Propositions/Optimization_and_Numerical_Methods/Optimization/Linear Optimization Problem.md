---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/linear_optimization
keywords:
  - linear_optimization
topics:
  - optimization/theory
  - optimization/algorithm
name: Linear Optimization Problem
date of note: 2024-08-15
---

## Concept Definition

>[!important]
>**Name**: Linear Optimization Problem

![[Convex Optimization Problem#^bc3f9c]]

![[Convex Optimization Problem#^423e21]]

- [[Convex Optimization Problem]]

>[!important] Definition
>A  **linear optimization problem** or **linear programming** of the form below
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>$$
>is said to be in **standard form**, where $x\in \mathbb{R}^{n}$, $\boldsymbol{A}\in \mathbb{R}^{m\times n}$ and $c\in \mathbb{R}^{n}.$

^099c2f

>[!important] Definition
>The **linear optimization problem** can be represented geometrically as 
>$$
>\begin{align*}
>\min_{x} \;\;& f(x) \\
>\text{s.t. }\;& x\in P
>\end{align*}
>$$
>where $f: \mathbb{R}^{d} \to \mathbb{R}$ is a **linear function** and $P \subset \mathbb{R}^{d}$ is a **polyhedron**.

- [[Bounded Linear Functional]]
- [[Linear Map]]
- [[Polyhedron and Polytope]]


>[!important]
>In linear optimization,
>- the **feasible region** $$\mathcal{D} := \left\{ x\in \mathbb{R}^{n}:   Ax \preceq b\right\} $$ is a **polyhedron**
>- and the **objective function** $$\left\langle c , x \right\rangle = \sum_{i=1}^{n}c_{i}x_{i}$$ is **linear function**.

- [[Polyhedron and Polytope]]

## Explanation

>[!important] 
>There are many forms of **linear programming**, as long as both **objective function** and **constraint functions** are **linear**.
>
>
>Another common form of linear programming is
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax \preceq b
\end{align*}
>$$


## Simplex Method

- [[Simplex Method for Linear Optimization]]


## Interior Point Method

- [[Barrier Method for Linear Optimization]]

## Integer Programming

- [[Integer Linear Optimization Problem and Integer Programming]]




-----------
##  Recommended Notes and References

- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]

- [[Convex Optimization Problem]]


- [[Simplex Method for Linear Optimization]]
- [[Barrier Method for Linear Optimization]]
- [[Primal-Dual Interior Point Method for Convex Optimization]]


- [[Convex Optimization by Boyd]]
- [[Introduction to Linear Optimization by Bertsimas]] pp 4
- [[Convex Analysis by Rockafellar]]