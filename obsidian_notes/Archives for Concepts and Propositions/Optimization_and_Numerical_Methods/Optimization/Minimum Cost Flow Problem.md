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
  - minimum_cost_flow
topics:
  - network_analysis
  - math/graph_theory
  - optimization/theory
name: Minimum Cost Flow Problem
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Minimum Cost Flow Problem

![[Network and Flow and Capacity and Cut#^9fa477]]
![[Network and Flow and Capacity and Cut#^4a27b4]]

![[Network and Flow and Capacity and Cut#^667ae1]]

![[Network Flow Problem as Linear Optimization#^1ce203]]

- [[Network Flow Problem as Linear Optimization]]

>[!important] Definition
>Let $f$ be a *flow* in a *network* $N := (G, s,t, u, c)$ with $G = (V, E)$. 
>- We denote the *flow function* along each *arc* as $$f_{i,j} := f(i,j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *total flow* that *enters* the network from outside at vertex $i$ as $b_{i}$
>- Denote the *capacity function* along each *arc* as $$u_{i,j} := u(i, j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *cost function* along each *arc* as $$c_{i,j} := c(i, j), \quad (e, i,j)\in \vec{E}$$
>  
>The **minimum cost flow problem** can be formulated as the following *linear optimization problem* 
>$$
>\begin{align*}
> \min_{\{ f_{i,j}\}_{(i,j)\in E}}\;&\; \sum_{(i,j)\in \vec{E}} c_{i,j}\,f_{i,j} \\[5pt]
> \text{s.t. }\;&\;b_{i} + \sum_{j\in \text{Pa}(i)}f_{j,i} = \sum_{k \in \text{Ch}(i)}f_{i,k}, \quad \forall i\in V \\[5pt]
> &\; b_{t} = -b_{s}\\[5pt]
> &\; b_{i} = 0,\quad \forall i\in V \setminus \{ s,t \}\\[5pt]
> &\; 0  \le f_{i,j} \le u_{i,j}, \quad \forall (e, i,j)\in \vec{E}
>\end{align*}
>$$ 

^19518d

- [[Linear Optimization Problem]]

### Transportation Cost Problem

>[!important] Definition
>Let $f$ be a *flow* in a *network* $N := (G, s,t, u, c)$ with $G = (V, E)$ and $G = \mathcal{S} \cup \mathcal{T}$ is a *bipartite graph*. 
>- We denote the *flow function* along each *arc* as $$f_{i,j} := f(i,j), \quad (e, i,j)\in \vec{E}$$
>- Denote the *total flow* that *enters* the network from outside at vertex $i$ as $b_{i}$
>- Denote the *source supply* as $$s_{i}, \quad i\in \mathcal{S}$$
>- Denote the *target demand* as $$d_{j}, \quad j\in \mathcal{T}$$
>- Denote the *cost function* along each *arc* as $$c_{i,j} := c(i, j), \quad (e, i,j)\in \vec{E}$$
>  
>The **minimum cost transportation problem** can be formulated as the following *linear optimization problem* 
>$$
>\begin{align*}
> \min_{\{ f_{i,j}\}_{(i,j)\in E}}\;&\; \sum_{i \in \mathcal{S}}\sum_{j \in \mathcal{T}} c_{i,j}\,f_{i,j} \\[5pt]
> \text{s.t. }\;&\;\sum_{i \in \mathcal{S}} f_{i,j} = d_{j}, \quad j\in \mathcal{T} \\[5pt]
> &\; \sum_{j \in \mathcal{T}} f_{i,j} = s_{i}, \quad i\in \mathcal{S} \\[5pt]
> &\; f_{i,j} \ge 0, \quad \forall (e, i,j)\in \vec{E}
>\end{align*}
>$$ 


- [[Optimal Assignment Problem and Monge Problem]]
- [[Optimal Transport in Discrete Setting]]
- [[Wasserstein Distance]]

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