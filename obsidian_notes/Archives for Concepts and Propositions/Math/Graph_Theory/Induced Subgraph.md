---
tags:
  - concept
  - math/graph_theory
keywords:
  - induced_subgraph
topics:
  - math/graph_theory
name: Induced Subgraph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Induced Subgraph

![[Graph Operations and Subgraph#^5e31a1]]

>[!important] Definition
>Let $G' = (V', E')$ and $G = (V, E)$.
>
>If 
>- $G' \subseteq G$ and 
>- $G'$ contains *all the edges* $xy\in E$ with $x,y \in V'$, 
>
>then $G'$ is an **induced subgraph** of $G$. 
>
>- we say that $V'$ **induces** or **spans** $G'$ in $G$, *induced subgraph* and write $$G' := G[V'].$$

^ab6014


>[!important] Definition
>If $U \subseteq V$ is any set of vertices, then $G[U]$ denotes the **graph on** $U$ whose *edges* are precisely *the edges of* $G$ with *both ends in* $U.$

>[!info]
>If $H$ is a *subgraph* of $G$, *not necessarily induced*, we abbreviate $G[V(H)]$ to $G[H]$.



## Explanation





-----------
##  Recommended Notes and References


- [[Graph Operations and Subgraph]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 4