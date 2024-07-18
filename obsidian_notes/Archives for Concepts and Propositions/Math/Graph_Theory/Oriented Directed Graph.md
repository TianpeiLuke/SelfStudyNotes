---
tags:
  - concept
  - math/graph_theory
keywords:
  - orientation_of_graph
  - oriented_directed_graph
topics:
  - math/graph_theory
name: Oriented Directed Graph
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Oriented Directed Graph

>[!important] Definition
>A *directed graph* $D$ is an **orientation** of an *undirected graph* $\mathcal{G}$ if 
>- $$V(D) = V(\mathcal{G});$$
>- $$E(D) = E(\mathcal{G});$$ 
>- and if for every edge $e=xy$, $$\{ \text{init}(e), \text{ter}(e)  \}  = \{ x, y \}$$
>  
>Intuitively, such an **oriented graph** arises from an undirected graph simply by *directing* *every edge* from one of its ends to the other. Put differently, *oriented graphs* are directed graphs **without loops** or **multiple edges**.

^1716d0

- [[Directed Acyclic Graph]]



## Explanation





-----------
##  Recommended Notes and References


- [[Directed Graph]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 28