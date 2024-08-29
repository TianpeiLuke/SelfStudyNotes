---
tags:
  - concept
  - optimization/multi-objective
keywords:
  - multi_objective_optimization
topics:
  - optimization
  - multi-objective_optimization
name: Multi-Objective Optimization Problem
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Multi-Objective Optimization Problem

![[Constrained Optimization Problem#^0430c8]]

![[Constrained Optimization Problem#^7c9083]]


>[!important] Definition
>The **multi-objective optimization problem** is defined as follows
>$$
>\begin{align*}
> \min_{x}\,&\; \min\left\{ f_{0,1}(x) \,{,}\ldots{,}\, f_{0,k}(x)\right\}\\[5pt]
> \text{s.t. }& x\in \mathcal{X}
>\end{align*}
>$$
>where each $f_{0,i}: \mathbb{R}^{d} \to \mathbb{R}$ represents an *objective function*.

^c437bf

### Dominated Solution and Pareto Front

>[!important] Definition
>Given $k$ objective functions $f_{0,i},\; i=1\,{,}\ldots{,}\,k$, a solution $x\in \mathcal{X}$ **dominates** a solution $y\in \mathcal{X}$ if
>- $x$ is *no worse* than $y$ in terms of *any* objectives $f_{0,i}$, i.e. $$f_{0,i}(x) \le f_{0,i}(y), \quad \forall i\in [k]$$
>- *and*  $x$ is *strictly better* than $y$ in terms of *some* objective,  $$f_{0,i}(x) < f_{0,i}(y) \quad \exists i\in [k]$$
>  
>Denote $x \succeq y$ when $x$ *dominates* $y$.  
>- A solution $x^{*}\in \mathcal{X}$ is called **non-dominated** if it is not dominated by any solution in $\mathcal{X}$. That is, $$y \succeq x^{*} \implies y\not\in \mathcal{X}$$
>- All nondominated solutions possess the attribute that their quality cannot be increased with respect to any of the objective functions without detrimentally affecting one of the others.
>- The set of *all nondominated solutions* is called the **Pareto set** or the **Pareto front**.

^9b6787

- [[Pareto Optimality and Pareto Dominate for Game Strategy]]
- [[Strict Partial Order Relation]]



## Explanation





-----------
##  Recommended Notes and References



- [[Nondominated Sorting Genetic Algorithm for Multi-Objective Optimization]]
- [[Pareto Optimality and Pareto Dominate for Game Strategy]]
- [[Constrained Optimization Problem]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 195 - 197