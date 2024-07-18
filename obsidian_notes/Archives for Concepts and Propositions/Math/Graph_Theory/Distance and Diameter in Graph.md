---
tags:
  - concept
  - math/graph_theory
keywords:
  - distance_graph
  - diameter_graph
  - radius_graph
topics:
  - math/graph_theory
name: Distance Diameter and Radius in Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Distance Diameter and Radius in Graph

>[!important] Definition
>Let $G$ be a graph. 
>
>The **distance** $d_{G}(x, y)$ in $G$ of two vertices $x,y$ is the *length of shortest $x$-$y$ path in $G.$* i.e. $$d_{G}(x, y) = \min\left\{ |P|: P = x \ldots y \right\}$$
>- If no such path exists $d_{G}(x, y) = \infty$

^031ab2

- [[Paths in Graph and Length of Path]]
- [[Metric Space]]

>[!important] Definition
>Let $G$ be a graph. 
>
>The **diameter** of $G$ is the *greatest distance* between any two vertices $x,y$ in $G$. $$\text{diam}(G) := \max\{d_{G}(x,y): \quad x,y\in G\}$$




## Explanation


## Property

>[!important] Proposition
>Every graph $G$ containing a **cycle** satisfies $$g(G) \le 2\,\text{diam}(G) + 1,$$ where $g(G)$ is the **girth** of $G$, or the *length of shortest cycle* in $G$.

- [[Girth and Circumference of Graph]]




-----------
##  Recommended Notes and References


- [[Girth and Circumference of Graph]]
- [[Cycles in Graph]]
- [[Paths in Graph and Length of Path]]
- [[Graph]]

- [[Metric Space]]



- [[Graph Theory by Diestel]] pp 8