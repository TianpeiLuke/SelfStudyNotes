---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - linear_optimization
  - reduced_cost
  - feasible_direction
topics:
  - optimization/algorithm
name: Feasible Direction for Linear Optimization
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

^670d89

- [[Polyhedron and Polytope]]

### Moving from one Basic Solution to Another 

![[Basic Solution for Linear Optimization#^52390c]]

- [[Basic Solution for Linear Optimization]]
- [[Extreme Points of Polyhedron]]
- [[Vertex Point of Polyhedron]]
- [[Active and Independent Constraints for Linear Optimization]]

![[Basic Solution for Linear Optimization#^2fb7eb]]


>[!info]
>Let $x$ be a **basic feasible solution** to the standard form problem, let $B(1) \,{,}\ldots{,}\, B(m)$ be the indices of the **basic variables**, and let $$B = [A_{B(1)} . . . A_{B(m)}]$$ be the corresponding **basis matrix**. 
>
>In particular, we have $x_i = 0$ for every *nonbasic variable*, while the vector $XB = (x_{B(1)}\,{,}\ldots{,}\,x_{B(m)})$ of basic variables is given by  $$x_{B} = B^{-1}b.$$

- [[Basic Solution for Linear Optimization]]





### Reduced Cost

>[!important] Definition
>Let $x$ be a *basic solution*, let $B$ be an *associated basis matrix*, and let $c_{B}$ be the *vector* of *costs of the basic variables*. 
>
>For each $j$, we define the **reduced cost** $\bar{c}_{j}$ of the variable $x_{j}$ according to the formula
>$$
>\bar{c}_{j} := c_{j} - \left\langle  c_{B}\,,\, B^{-1}A_{j} \right\rangle
>$$

^6f654f




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