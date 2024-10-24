---
tags:
  - concept
  - math/graph_theory
keywords:
  - graph
  - network_graph
  - network_flow_optimization
  - network_flow
  - cut_graph
  - flow_graph
  - capacity_cut
  - capacity_network
topics:
  - math/graph_theory
name: Network and Flow and Capacity
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Network and Flow and Capacity and Cut

![[Edge Orientiations#^1610ae]]

>[!important] Definition
>Let $G = (V, E)$ be a mutigraph, and $s,t\in V$ be two fixed vertices. 
>- Define the **capacity function** on $G$ as $$c: \vec{E} \to \mathbb{N}$$  
>- The *quadruple* $$N := (G, s,t, c)$$ is called a **flow network** or a **network.** 
>	- Note that the *capacity function* is defined independently from the *two orientations* of an edge.
>- The vertex $s$ is called a **source** and $t$ is called a **sink**.

^9fa477

- [[Edge Orientiations]]

>[!important] Definition
>Let $N := (G, s,t, c)$ be the *network* with graph $G = (V, E)$, $s,t\in V$ and *capacity function* $c$ on $G$.
>
>A function $$f: \vec{E} \rightarrow \mathbb{R}$$ is called a **flow** in network $N$ if it satisfies the following **three conditions**:
>- **Skew symmetry constraint**: The *flow* on an arc from $x$ to $y$ is equivalent to the *negation of the flow* on the arc from $y$ to $x$, $$f(e, x, y) = - f(e, y, x), \quad \forall (e,x, y)\in \vec{E},\, x\neq y$$
>- **Flow conservation constraint**: The *total net flow* *entering* a node $v$ is zero for all nodes in the network except the source $s$ and sink $t$, $$f(v, V) = 0,\quad \forall v\in V \setminus \{ s, t \}$$
>- **Capacity constraint**: the flow on each arc does *not exceed* the *capacity* of the edge $$f(\vec{e}) \le c(\vec{e}), \quad \forall \vec{e} \in \vec{E}$$
>  
>We call $f$ **integral** if all its values are *integers*.  

^4a27b4

- [[Circulation of Graph]]

>[!important] Definition
>Let $f$ be a flow in $N := (G, s,t,c)$ with $G = (V, E)$. 
>
>If $S \subset V$ is such that 
>- the source $s\in S$, and 
>- the sink $t\in \bar{S} := V \setminus S$, 
>
>then the pair $$(S, \bar{S})$$ is called a **cut** or **cut-set**.
>
>The **capacity of a cut** is the total capacity of all arcs from $S$ to $\bar{S}$, i.e. $$c(S, \bar S) := \sum_{\vec{e} \in \vec{E}(S, \bar{S})}\,c(\vec{e}).$$

^667ae1

## Explanation


## Flow Condition as Linear Constraint



## Capacity of Cut-Set as Linear Function







-----------
##  Recommended Notes and References


- [[Max-Flow Min-Cut Theorem]]
- [[Maximum Flow Problem]]
- [[Graph]]
- [[Linear Optimization Problem]]

- [[Graph Theory by Diestel]] pp 149 - 150
- Wikipedia [Flow_network](https://en.wikipedia.org/wiki/Flow_network)