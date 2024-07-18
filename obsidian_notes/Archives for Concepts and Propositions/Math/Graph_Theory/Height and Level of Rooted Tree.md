---
tags:
  - concept
  - math/graph_theory
keywords:
  - height_rooted_tree
  - level_rooted_tree
topics:
  - math/graph_theory
name: Height and Level of Rooted Tree
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Height and Level of Rooted Tree

![[Tree Graph and Forest#^90f857]]

![[Distance and Diameter in Graph#^031ab2]]

>[!important] Definition
>Let $(T, r)$  be a rooted tree with root $r$.
>
>The vertices *at distance* $k$ from the root have **height** $k$, i.e.
>$$
> \text{height}(v) =  d_{T}(r, v)
>$$
>
>The **level $k$** of the rooted tree $(T, r)$ is the set of all vertices that have height $k$
>$$
>\text{level}_{T}(k) := \left\{ v\in T:  d_{T}(r, v) = k\right\} = d_{T,r}^{-1}(\left\{ k \right\})
>$$

- [[Distance and Diameter in Graph]]

## Explanation





-----------
##  Recommended Notes and References


- [[Tree-Order Relation]]
- [[Tree Graph and Forest]]

- [[Paths in Graph and Length of Path]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 15