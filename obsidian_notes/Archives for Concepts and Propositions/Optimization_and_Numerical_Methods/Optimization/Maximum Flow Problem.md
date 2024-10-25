---
tags:
  - concept
  - math/graph_theory
  - optimization
  - optimization/algorithm
  - optimization/theory
  - math/optimal_transport
  - algorithm/graph
  - optimization/linear_optimization
keywords:
  - maximum_flow
topics:
  - network_analysis
  - math/graph_theory
  - optimization/theory
name: Maximum Flow Problem
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Maximum Flow Problem

![[Network and Flow and Capacity and Cut#^9fa477]]
![[Network and Flow and Capacity and Cut#^4a27b4]]

![[Network and Flow and Capacity and Cut#^667ae1]]

![[Network Flow Problem as Linear Optimization#^1ce203]]

- [[Network Flow Problem as Linear Optimization]]

>[!important] Definition
>Let $f$ be a *flow* in a *network* $N := (G, s,t, u)$ with $G = (V, E)$. 
>- We denote the *flow function* along each *arc* as $$f_{i,j} := f(i,j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *total flow* that *enters* the network from outside at vertex $i$ as $b_{i}$
>- Denote the *capacity function* along each *arc* as $$u_{i,j} := u(i, j), \quad (e, i,j)\in \vec{E}$$
>  
>The **maximum flow problem** can be formulated as the following *linear optimization problem* 
>$$
>\begin{align*}
> \max_{\{ f_{i,j}\}_{(i,j)\in E}}\;&\; b_{s} \\[5pt]
> \text{s.t. }\;&\;b_{i} + \sum_{j\in \text{Pa}(i)}f_{j,i} = \sum_{k \in \text{Ch}(i)}f_{i,k}, \quad \forall i\in V \\[5pt]
> &\; b_{t} = -b_{s}\\[5pt]
> &\; b_{i} = 0,\quad \forall i\in V \setminus \{ s,t \}\\[5pt]
> &\; 0  \le f_{i,j} \le u_{i,j}, \quad \forall (e, i,j)\in \vec{E}
>\end{align*}
>$$ 

^19518d

- [[Max-Flow Min-Cut Theorem]]
- [[Linear Optimization Problem]]

>[!important] Definition
>The constraint set can be reformulated in matrix form
>$$
>A f = b
>$$
>where 
>- the **node-arc incidence matrix** is defined as $$A = [a_{i,k}] \in \mathbb{R}^{|V| \times |E| }, \quad a_{i,k} = \left\{\begin{array}{cl}1 & \text{ if node }i \text{ is the start of k-th  arc} \\[5pt] -1 & \text{ if node }i \text{ is the end of k-th  arc} \\[5pt] 0 & \text{ otherwise }\end{array} \right.$$


## Explanation





-----------
##  Recommended Notes and References


- [[Network and Flow and Capacity and Cut]]
- [[Max-Flow Min-Cut Theorem]]
- [[Graph]]

- [[Network Flow Problem as Linear Optimization]]



- [[Introduction to Linear Optimization by Bertsimas]] pp 301
- [[Graph Theory by Diestel]] pp 141, 171
- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]