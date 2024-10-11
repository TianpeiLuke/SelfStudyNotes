---
tags:
  - concept
  - algorithm
  - algorithm/dynamic_programming
  - optimization/theory
  - optimization/algorithm
  - probabilistic_graphical_models/algorithm
  - evolutionary_computation
keywords:
  - integer_programming_problem
  - integer_optimization_problem
topics:
  - optimization/theory
  - optimization/algorithm
name: Integer Programming Problem
date of note: 2024-08-19
---

## Concept Definition

>[!important]
>**Name**: Integer Programming Problem

![[Linear Optimization Problem#^099c2f]]


>[!important] Definition
>A **standard form** of  **integer linear optimization problem** or **integer programming** is of the form below
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;&\; Ax = b\\
>\;&\;x \succeq 0\\
>\;&\;x\in \mathbb{Z}^{n}
\end{align*}
>$$
>iwhere the optimization variables $x\in \mathbb{Z}^{n}$ is integers, $A\in \mathbb{R}^{m\times n}$, $b\in \mathbb{R}^{m}$  and $c\in \mathbb{R}^{n}.$

- [[Linear Optimization Problem]]

>[!important] Definition
>A  **mixed-integer programming** is of the form below
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;&\; Ax = b\\
>\;&\;x \succeq 0\\
>\;&\;x_{i}\in \mathbb{Z}\quad i\in \mathcal{I}_{i}\\
>&\;x_{j} \in \mathbb{R}\quad j\in \mathcal{I}_{r},
\end{align*}
>$$
>where $\mathcal{I}_{i} \cup \mathcal{I}_{r} = [n]$, $A\in \mathbb{R}^{m\times n}$, $b\in \mathbb{R}^{m}$ and $c\in \mathbb{R}^{n}.$


## Explanation

>[!info]
>Some *Integer Programming* problem can be formulated as **quadratic programming (QP)** with **indefinite matrix**.

- [[Quadratic Programming]]


## Algorithms that Solves Integer Programming


### Heuristic-based Search

- [[Backtracking]]

### Evolutionary Computation

- [[Theory and Algorithms for Gradient-Free Optimization]]
- [[Genetic Algorithms]]
- [[Genetic Programming]]
- [[Evolutionary Strategies]]
- [[Evolutionary Programming]]
- [[Natural Evolutionary Strategies]]
- [[Cross-Entropy Method for EDA]]


## NP Problems that are Integer Programming

- [[Knapscak Problem]]
- [[Set Cover Problem]]
- [[Traveling Salesman Problem]]
- [[Maximum Cut Problem]]
- [[Constraint Satisfaction Problem CSP]]


## Graphical Models

- [[Maximum A Posteriori Probability Query of Graphical Model]]




-----------
##  Recommended Notes and References










- [[Introduction to Linear Optimization by Bertsimas]] pp 451
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Graphical Models by Koller]]