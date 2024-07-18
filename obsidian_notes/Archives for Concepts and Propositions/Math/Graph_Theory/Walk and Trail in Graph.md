---
tags:
  - concept
  - math/graph_theory
keywords:
  - walk_in_graph
topics:
  - math/graph_theory
name: Walk in Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Walk in Graph

>[!important] Definition
>A **walk** *of length* $k$ in a graph $G$ is a non-empty **alternating sequence** $$v_{0}e_{0}v_{1}e_{1}\,{}\ldots{}\,e_{k-1}v_{k}$$ of *vertices* and *edges* in $G$ such that $e_{i} = \left\{ v_{i}, v_{i+1} \right\}$ for all $i < k.$
>- If $v_{0} = v_{k}$, then the *walk* is **closed**.

>[!important] Definition
>A **trail** in a graph $G$ is a *walk* in which all *edges* are *distinct*.



## Explanation

>[!important] Proposition
>Every **walk** between two vertices contains a **path** between these vertices.

- [[Paths in Graph and Length of Path]]



-----------
##  Recommended Notes and References

- [[D-Separation in Graphical Model]]

- [[Paths in Graph and Length of Path]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 8
- Wikipedia [Path_(graph_theory)](https://en.wikipedia.org/wiki/Path_(graph_theory))