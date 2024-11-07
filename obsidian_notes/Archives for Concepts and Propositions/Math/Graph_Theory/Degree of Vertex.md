---
tags:
  - concept
  - math/graph_theory
keywords:
  - degree_vertex
topics:
  - math/graph_theory
name: Degree of Vertex
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Degree of Vertex

>[!important] Definition
>Let $G = (V, E)$ be a *non-empty graph*. 
>
>- The *set of neighbors* of a vertex $v\in V$ in $G$ is denoted as $$N_{G}(v) \quad \text{ or briefly } \quad N(v).$$ 
>- More generally for $U \subseteq V$, the neighbors in $V \setminus U$ *of vertices in* $U$ are called **neighbors of $U$.** It is denoted as $$N(U).$$


>[!important] Definition
>The **degree or valency** of a vertex $v$ is *the number edges at* $v$, i.e. $$d_{G}(v) = d(v) := |E(v)| = |N(v)|.$$ 
>
>It is equal to the *number of neighbors* of $v$.

^75a6dd

- [[Graph]]

>[!important] Definition
>A vertex of degree $0$ is called an **isolated vertex**.

>[!important] Definition
>Let $G = (V, E)$ be a *non-empty graph*. 
>
>- The **minimum degree** of $G$ is defined as $$\delta(G) := \min\left\{ d(v): v\in V \right\} $$
>- The **maximum degree** of $G$ is defined as $$\Delta(G) := \max\left\{ d(v): v\in V \right\} $$
>- The **average degree** of $G$ is defined as $$d(G) := \frac{1}{|V|}\sum_{v\in V}d(v).$$
>- Define the *ratio* of total edges and total vertices as $$\epsilon(G) := \frac{|E|}{|V|}.$$
>  
>Clearly $$\delta(G) \le d(G) \le \Delta(G).$$  

>[!important] 
>If we *sum up all the vertex degrees* in $G$, we count *every edge exactly twice*: once from each of its ends. That is
>$$
>|E| = \frac{1}{2}\sum_{d\in V}d(v) = \frac{1}{2}d(G) \cdot |V|
>$$
>Therefore
>$$
>\epsilon(G) = \frac{1}{2}d(G).
>$$



## Explanation





-----------
##  Recommended Notes and References

- [[Complete Graph Clique and Triangle]]

- [[Adjacency Matrix of Graph]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 5 - 6
- [[Networks by Newman]] pp 126 - 131