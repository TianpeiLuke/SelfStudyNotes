---
tags:
  - concept
  - optimization/theory
  - math/information_theory
  - math/optimal_transport
keywords:
  - optimal_transport
  - optimal_assignment
  - monge_problem
topics:
  - information_theory
  - optimal_transport
name: Optimal Assignment Problem
date of note: 2024-08-26
---

## Concept Definition

>[!important]
>**Name**: Optimal Assignment Problem

>[!important] Definition
>Let $C \in \mathbb{R}^{n\times m}$ be a *cost matrix*, where each entry $c_{i,j} >0$ represents 
>- the cost of *assigning* the *task* $x_{i}$ to *individual* $y_{j}$;
>- or the cost of *moving mass* from *location* $x_{i}$ to $y_{j}$. 
>
>Also
>- Let $a := (a_{1} \,{,}\ldots{,}\,a_{n})$  be the *initial task configuration* or mass at *source* $x$, and 
>- let $b := (b_{1} \,{,}\ldots{,}\,b_{m})$ be the *final assignment* or mass at *destination* $y$.
>  
>The **Monge problem** or **optimal assignment problem** seeks a map $$T: \left\{ x_{1} \,{,}\ldots{,}\, x_{n}\right\} \to \left\{ y_{1} \,{,}\ldots{,}\, y_{m}\right\}$$ such that 
>- for each *individual* or *final destination* $j=1\,{,}\ldots{,}\,m$, $$b_{j} = \sum_{i: T(x_{i}) = y_{j}}a_{i}$$
>- And such map $T$ should minimize the *total cost of assignment*.
>
>We can formulate this problem as the *combinatorial optimization problem*
>$$
>\begin{align*}
> \min_{T}\;&\; \sum_{i=1}^{n}c\left( x_{i}, T(x_{i})\right) \\[5pt]
> \text{ s.t. }& b_{j} = \sum_{i: T(x_{i}) = y_{j}}a_{i}, \quad j=1\,{,}\ldots{,}\,m
>\end{align*}
>$$  
>Here
>- we can define the *discrete measures* as $$\alpha := \sum_{i=1}^{n}a_{i}\delta_{x_{i}}, \quad \beta := \sum_{j=1}^{m}b_{j}\,\delta_{y_{j}}.$$
>- then the assignment constraint can be written by the *pushforward operation*  $$T_{*}\alpha = \beta$$

^6219c2

- [[Discrete Measure]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Optimal Transport in Discrete Setting]]

>[!important] Definition
>The **Monge-Kantorovich optimal transport problem** is a measure-theoretical  formulation of optimal assignment problem
>$$
>\inf\left\{ \int_{\mathcal{X}}c(x, T(x))\,d\mu:\; T_{*}\mu = \nu \right\} 
>$$
>where
>- $\mathcal{X}, \mathcal{Y}$ are two *separable metric measureable space (measurable Polish space)*
>- $\mu, \nu$ are *regular probability measures (Radon measures)* on $\mathcal{X}$ and $\mathcal{Y}$
>- $c: \mathcal{X}\times \mathcal{Y} \to [0, \infty)$ is *Borel-measurable function*
>- $T: \mathcal{X} \to \mathcal{Y}$ is a measurable function called the **transport map**.
>- $T_{*}$ is the *push-forward operator* induced by $T$ from measure on $\mathcal{X}$ to measure on $\mathcal{Y}$

^aa7704

- [[Polish Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Borel Measure]]
- [[Radon Measure]]
- [[Measurable Function]]
- [[Optimal Transport in Space of Measures]]


## Explanation

>[!info]
>In optimal assignment problem, it requires that **at most one** agent should be assigned to **each task** and **at most one task** to **each agent**.


>[!info]
>The assignment problem consists of finding, in a **weighted bipartite graph**, a **matching** of a given size, in which the *sum of weights* of the edges is *minimum*.

- [[Bipartite Graph]]
- [[Matching in Vertex and Edge of Graph]]

>[!important]
>The optimal assignment problem is a fundamental **combinatorial optimization problem**.

- [[Combinatorial Optimization Problem]]


## Kantorovich Relaxation

>[!info]
>If we allow a task to be **split** into fractions to **multiple individuals**, this problem can be reformulated into a *linear programming problem*, called the **optimal transportation problem.**

- [[Optimal Transport in Discrete Setting]]
- [[Linear Optimization Problem]]
- [[Optimal Transport in Space of Measures]]

## Algorithms that Approximately Solve the Optimal Assignment

- [[Optimal Transport in Discrete Setting]]
- [[Wasserstein Distance]]
- [[k-Means Clustering]]


## NP Problem

- [[Constraint Satisfaction Problem CSP]]



-----------
##  Recommended Notes and References


- [[k-Means Clustering]]
- [[Optimal Transport in Discrete Setting]]
- [[Optimal Transport in Space of Measures]]
- [[Integer Linear Optimization Problem and Integer Programming]]
- [[Combinatorial Optimization Problem]]


- [[Matching in Vertex and Edge of Graph]]
- [[Bipartite Graph]]


- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 307
- [[Graph Theory by Diestel]]
- Wikipedia [Assignment_problem](https://en.wikipedia.org/wiki/Assignment_problem)
- Wikipedia [Transportation_theory_(mathematics)](https://en.wikipedia.org/wiki/Transportation_theory_(mathematics))
