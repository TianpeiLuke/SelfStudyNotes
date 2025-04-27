---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - proximal_algorithm
keywords:
  - proximal_algorithm
topics:
  - optimization/algorithm
name: Proximal Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Proximal Algorithm

![[Approximation Method for Optimization#^9a898b]]


>[!important] Definition
>Let $f: \mathbb{R}^{n} \to (-\infty, \infty]$ be a **closed convex function**.
>
>The **proximal algorithm** (or, the **proximal minimization algorithm** or **proximal point algorithm**) is an approximate method, where at each iteration $k$, $x_{k+1}$ solve the following optimization problem
>$$
>x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\} 
>$$

^258191

- [[Convex Optimization Problem]]
- [[Strongly Convex Function]]

## Explanation


- [[Greedy Heuristic Algorithms]]

## Proximal Type Algorithms

- [[Dual Proximal Algorithm]]
- [[Augmented Lagrangian Algorithm]]
- [[Proximal Gradient Algorithm]]
- [[Dual Proximal Gradient Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]

>[!quote]
>Thus all three *proximal-type methods*, 
>- **proximal gradient**, 
>- **ADMM**, and 
>- **augmented Lagrangian**, 
>
>have *similarities*, and **relative strengths** and **weaknesses**. The choice between them hinges largely on the given problem's structure.
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 337



-----------
##  Recommended Notes and References


- [[Approximation Method for Optimization]]
- [[Proximal Gradient Algorithm]]
- [[Augmented Lagrangian Algorithm]]
- [[Augmented Lagrangian Function]]
- [[Alternating Direction Method of Multipliers Algorithm]]


- [[Convex Optimization Algorithms by Bertsekas]] pp 234