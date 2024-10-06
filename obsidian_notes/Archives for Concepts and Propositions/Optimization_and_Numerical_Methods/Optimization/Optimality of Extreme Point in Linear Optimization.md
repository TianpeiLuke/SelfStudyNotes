---
tags:
  - concept
  - optimization/theory
  - optimization/linear_optimization
keywords:
  - extreme_points
  - polyhedral_set
  - linear_optimization
  - optimal_solution
topics:
  - optimization/theory
name: Optimality of Extreme Point in Linear Optimization
date of note: 2024-08-17
---

## Concept Definition

>[!important]
>**Name**: Optimality of Extreme Point in Linear Optimization

>[!important] Theorem
>Consider the **linear programming problem**
>$$
>\begin{align*}
> \min_{x} \;& \left\langle  c\,,\, x   \right\rangle\\
> \text{ s.t. }& x \in P
>\end{align*}
>$$
>where $P$ is a *polyhedron*.
>
 >Suppose that $P$ has **at least one extreme point** and that there *exists* an **optimal solution**. 
 >
 >Then, there exists an **optimal solution** which is an **extreme point** of $P$.

- [[Linear Optimization Problem]]
- [[Extreme Points of Polyhedron]]
- [[Polyhedron and Polytope]]

>[!important] Theorem
>Consider the linear programming problem 
>$$
>\begin{align*}
> \min_{x} \;& \left\langle  c\,,\, x   \right\rangle\\
> \text{ s.t. }& x \in P
>\end{align*}
>$$ 
>
>Suppose that $P$ has **at least one extreme point.** 
>
>Then, **either** the **optimal cost** is equal to $-\infty$, or there **exists an extreme point** which is **optimal**.


>[!important] Corollary
>Consider the linear programming problem
>$$
>\begin{align*}
> \min_{x} \;& \left\langle  c\,,\, x   \right\rangle\\
> \text{ s.t. }& x \in P
>\end{align*}
>$$ 
 >where $P$ is non-empty polyhedron.
 >
 >Then, **either** the **optimal cost** is equal to $-\infty$ or there **exists an optimal solution**.

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]


## Explanation


## Lemma for Krein-Milman Theorem

![[Krein-Milman Lemma and Krein-Milman Theorem#^5c9b4d]]

- [[Krein-Milman Lemma and Krein-Milman Theorem]]


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