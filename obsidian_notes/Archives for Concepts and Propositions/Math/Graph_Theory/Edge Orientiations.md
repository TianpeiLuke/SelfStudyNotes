---
tags:
  - concept
  - math/graph_theory
keywords:
  - edge_orientations
topics:
  - math/graph_theory
name: Edge Orientiations
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Circulation of Graph

>[!important] Definition
>Let $G = (V, E)$ be an *undirected multigraph*. 
>- Every edge $xy\in E$ has **two directions** $(x, y)$ and $(y, x)$
>- A *triple* $(e, x, y)$ consists of an edge together with *one of its directions* is an **oriented edge** or an **arc**.
>- The *oriented edges* corresponding to $e$ are its **orientations**, denoted as $\overrightarrow{e}$,  $\overleftarrow{e}$. Thus $$\{\overrightarrow{e},\,\overleftarrow{e}   \} := \left\{ (e, x, y),\, (e, y, x) \right\} $$
>- We write $$\vec{E} = \left\{ (e, x, y) \;|\; e\in E,\, x,y\in V,\, e= xy \right\} $$ for the **set of all oriented edges**
>- We denote $$\overleftarrow{F} := \{ \overleftarrow{e}\;|\; \overrightarrow{e} \in \overrightarrow{E} \} $$
>- For $\vec{F} \subseteq \vec{E}$, we define **the set of all arcs from subset** $X$ **to** $Y$ as $$\vec{F}(X, Y) := \{ (e, x, y) \in \vec{F} \;|\; x\in X,\, y\in Y,\, x\neq y \}$$
>- Denote **the set of all arcs from a vertex to a subset** $$\vec{F}(x, Y) := \vec{F}(\{ x \}, Y)$$ 
>- We abbreviate the set of **all arcs from a vertex to all other vertices** $$\vec{F}(x) := \vec{F}(x, V)  := \vec{F}(\{ x \}, \overline{\{ x \}})$$ 

^1610ae

- [[Oriented Directed Graph]]


## Explanation





-----------
##  Recommended Notes and References


- [[Directed Acyclic Graph]]
- [[Directed Graph]]
- [[Network and Flow and Capacity and Cut]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 150