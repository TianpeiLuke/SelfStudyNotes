---
tags:
  - concept
  - math/graph_theory
keywords:
  - central_vertex
  - radius_graph
topics:
  - math/graph_theory
name: Central Vertex and Radius in Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Central Vertex and Radius in Graph

![[Distance and Diameter in Graph#^031ab2]]


>[!important] Definition
>A vertex is **central** in $G$ if its *greatest distance* from any other vertex is *as small as possible*.
>$$
>\text{x}_{central} \in \arg\min\left\{\max_{y\in V} d_{G}(x, y):\, x\in V \right\}
>$$

- [[Distance and Diameter in Graph]]

>[!important] Definition
>The **radius** of a graph $G$ is the *min-max of distance* between *any two vertices* in the graph
>$$
>\text{rad}(G) = \min_{x\in V}\max_{y\in V} d_{G}(x, y).
>$$

## Explanation

>[!important]
>We see that
>$$
>\text{rad}(G) \le \text{diam}(G) \le 2\,\text{rad}(G).
>$$

- [[Distance and Diameter in Graph]]

>[!info]
>Diameter and radius are **not related** to *minimum, average or maximum degree* if we say nothing about the *order* of the graph.

## Property

>[!important] Proposition
>A graph $G$ of **radius at most** $k$ and **maximum degree at most** $d \ge 3$ has **fewer than** $\frac{d}{d-2}(d-1)^{k}$ vertices.
>
>$$
>\text{rad}(G) \le k,\; \Delta(G) \le d, \; \implies |G| \le \frac{d}{d-2}(d-1)^{k} 
>$$

- [[Degree of Vertex]]
- [[Graph Theory by Diestel]] pp 9

>[!info]
>Let $z$ be a central node in $G$. Let $D_{i}$ denote the set of vertices in $G$ *at distance* $i$ from $z.$
>
>- $|D_{0}| = 1$
>- $|D_{1}| = d(z) \le d$
>
>We can show that
>$$
>|D_{i+1}| \le (d-1)\,|D_{i}|.
>$$
>Since 
>$$
>V(G) = \bigcup_{i=0}^{\text{rad}(G)}D_{i} 
>$$
>we have 
>$$
>| G | \le 1 + d\left( \sum_{i=0}^{k-1}(d-1)^{i} \right)
>$$



>[!important] Theorem (Alon, Hoory and Linial)
>Let $G$ be a graph. 
>
>If $d(G) \ge d \ge 2$, and $g(G) \ge g \in \mathbb{N}$, then $$|G| \ge n_{0}(d, g),$$
>where 
>$$
>\begin{align}
>n_{0}(d, g) := \left\{\begin{array}{cc}
> 1 + d\,\sum_{i=0}^{r-1}\left( d - 1 \right)^i\, & g= 2r + 1 \text{ odd}\\[5pt]
> 2 \sum_{i=0}^{r-1}\left( d - 1 \right)^i\, & g= 2r \text{ even}
>\end{array}
>\right.
\end{align}
>$$

- [[Degree of Vertex]]
- [[Girth and Circumference of Graph]]

>[!info]
>One aspect of Theorem above is that it guarantees the **existence** of a **short cycle** compared with $|G|$.


>[!important] Corollary
>Let $G$ be a graph. 
>
>If $\delta(G) \ge 3$, then $$g(G) < 2 \log|G|.$$




-----------
##  Recommended Notes and References




- [[Cycles in Graph]]
- [[Paths in Graph and Length of Path]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 8 - 9