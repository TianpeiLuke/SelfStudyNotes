---
tags:
  - concept
  - math/graph_theory
keywords:
  - edge_connectivity
  - l_edge_connected
topics:
  - math/graph_theory
name: Edge Connectivity of Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Edge Connectivity of Graph

![[Connectivity of Graph#^695a0c]]


>[!important] Definition
>If $|G| > 1$ and $G - F$ is *connected* for each edge set $F \subseteq\, E$ of *fewer than* $\ell$ edges, then $G$ is called **$\ell$-edge-connected**.

>[!important] Definition
>The *greatest integer* such that $G = (V, E)$ is *$\ell$-edge-connected* is the **edge-connectivity** of $G$. 
>
>It is denoted as $$\lambda(G) := \max\left\{ \ell: \; G - F \text{ connected } \forall F \subseteq\, E \text{ such that }|F| \le \ell \right\}.$$



## Explanation

>[!info]
>The edge connectivity $\lambda(G)$ is the **largest number of edges** that we can **delete** from $G$ so that the remaining graph is still *connected*.

## Property

>[!important] Proposition
>If $G$ is non-trivial, then $$\kappa(G) \le \lambda(G) \le \delta(G)$$

- [[Degree of Vertex]]
- [[Connectivity of Graph]]




-----------
##  Recommended Notes and References

- [[Connectivity of Graph]]
- [[Separation of Graph]]
- [[Connected Graph and Connected Component of Graph]]

- [[Graph Operations and Subgraph]]
- [[Graph]]
- [[Graph Theory by Diestel]] pp 12