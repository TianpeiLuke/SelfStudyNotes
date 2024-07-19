---
tags:
  - concept
  - math/graph_theory
keywords:
  - connected_graph
  - k_connected_graph
topics:
  - math/graph_theory
name: k-Connected Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Connectivity of Graph

>[!important] Definition
>A graph $G = (V, E)$ is called **$k$-connected** for $k\in \mathbb{N}$ if 
>- $|G| > k$ and
>- $G - X$ is *connected* for every vertex set $X \subseteq\, V$ with $|X| < k$
>  
>In other word, *no two* vertices of $G$ are *separated* by fewer than *$k$ other vertices*.  

^695a0c

- [[Graph Operations and Subgraph]]
- [[Connected Graph and Connected Component of Graph]]
- [[Separation of Graph]]

>[!important] Definition
>The *greatest integer* $k$ such that $G$ is *$k$-connected* is the **connectivity** of graph $G$. It is denoted as $$\kappa(G) = \max\left\{ k:  G - X \text{ connected } \forall X \subset V \text{ such that }|X| < k \right\}.$$

## Explanation

>[!info]
>The *connectivity* $\lambda(G)$ is the **largest number of vertices** that we can **delete** from $G$ so that the remaining graph is still *connected*.


>[!info]
>- $\kappa(G) = 0$ if and only if $G$ is disconnected, or a $K^1$
>- $\kappa(K^n) = n - 1$ for $n \ge 1$

- [[Complete Graph Clique and Triangle]]



-----------
##  Recommended Notes and References

- [[Edge Connectivity of Graph]]

- [[Separation of Graph]]
- [[Graph]]
- [[Graph Theory by Diestel]] pp 12
- Wikipedia [Connectivity_(graph_theory)](https://en.wikipedia.org/wiki/Connectivity_(graph_theory))