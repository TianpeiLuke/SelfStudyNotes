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
  - network_flow_optimization
  - maximum_flow
  - minimum_cut
topics:
  - optimization/theory
  - optimization/algorithm
name: Network Flow Problem as Linear Optimization
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Network Flow Problem as Linear Optimization

![[Network and Flow and Capacity and Cut#^9fa477]]
![[Network and Flow and Capacity and Cut#^4a27b4]]

![[Network and Flow and Capacity and Cut#^667ae1]]

>[!important] Definition
>Let $f$ be a *flow* in a *network* $N := (G, s,t,u, c)$ with $G = (V, E)$. 
>- We denote the *flow function* along each *arc* as $$f_{i,j} := f(i,j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *total flow* that *enters* the network from outside at vertex $i$ as $b_{i}$, $$b_{i} := f(i, V)$$
>- Denote the *capacity function* along each *arc* as $$u_{i,j} := u(i, j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *cost per unit* of flow along the arc as $$c_{i,j} := c(i, j), \quad (e, i,j)\in \vec{E}$$
>- The **constraints** for *flow* is formulated as $$\begin{align*} \text{ Flow Conservation:} \quad &\; b_{i} + \sum_{j\in \text{Pa}(i)}f_{j,i} = \sum_{k \in \text{Ch}(i)}f_{i,k}, \quad \forall i\in V \\[5pt] \text{ Capacity Constraint:} \quad &\; 0 \le f_{i,j} \le c_{i,j}, \quad (e, i,j)\in \vec{E}\end{align*}$$ 
>	- A flow $\{ f_{i,j} \}$ satisfies above constraints is called a **feasible flow.**
>	- Sum over $i\in V$ on first constraint, we have $$\sum_{i\in V}b_{i} = 0$$ That is, the total flow **into** the network from outside is equal to the flow **out of** the network to outside.
>	- Thus $$b_{s} = - b_{t}, \quad b_{v} = 0,\,\forall v\in V \setminus \{ s,t \}$$

^1ce203

- [[Network and Flow and Capacity and Cut]]
- [[Maximum Flow Problem]]

### Maximum Flow Problem

![[Maximum Flow Problem#^19518d]]

- [[Maximum Flow Problem]]
- [[Linear Optimization Problem]]

### Minimum Cost Network Flow Problem

![[Minimum Cost Flow Problem#^19518d]]

- [[Minimum Cost Flow Problem]]





## Explanation





-----------
##  Recommended Notes and References



- [[Network and Flow and Capacity and Cut]]
- [[Max-Flow Min-Cut Theorem]]
- [[Graph]]

- [[Optimal Transport in Discrete Setting]]
- [[Wasserstein Distance]]


- [[Introduction to Linear Optimization by Bertsimas]] pp 272 - 302
- [[Graph Theory by Diestel]] pp 141, 171
- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]