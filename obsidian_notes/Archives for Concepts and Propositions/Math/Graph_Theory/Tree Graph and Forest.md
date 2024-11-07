---
tags:
  - concept
  - math/graph_theory
keywords:
  - tree_graph
  - forest_graph
topics:
  - math/graph_theory
name: Tree Graph and Forest
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Tree Graph and Forest

>[!important] Definition
>A graph *without any cycles* is called an **acyclic graph**, or **forest**.
>
>A *connected forest* is called a **tree**.


^90f857

- [[Cycles in Graph]]
- [[Connected Graph and Connected Component of Graph]]


>[!important] Definition
>The vertices of *degree* $1$ in a tree are its **leaves**, the others are its **inner vertices**.

- [[Degree of Vertex]]




## Explanation


## Criterion of Tree

>[!important] Theorem
>The following assertions are *equivalent* for a graph $T$:
>- $T$ is a **tree**;
>- Any two vertices of $T$ are linked by a **unique path** in $T$.
>- $T$ is **minimally connected**, i.e. $T$ is *connected*, but $T - e$ is *disconnected* for *every edge* $e\in T$.
>- $T$ is **maximally acyclic**, i.e. $T$ contains no *cycle*, but $T + xy$ does contain an cycle for any two *non-adjacent vertices* $x, y\in T.$

^4f77eb

- [[Graph Operations and Subgraph]]
- [[Paths in Graph and Length of Path]]
- [[Connectivity of Graph]]


>[!important] Definition
>Since the path from $x \to y$ in $T$ is unique, we denote the **unique path** *from* $x$ to $y$ as $xTy$.

>[!important] 
>A common application of above theorem is that every *connected graph* contains a **spanning tree**.

- [[Spanning Tree and Chord]]

>[!important] Corollary
>The vertices of a tree can always be **enumerated**, say as $$v_{1}\,{}\ldots{}\,v_{n},$$ so that every $v_{i}$ with $i \ge 2$ has a **unique neighbor** in $\left\{ v_{1}\,{,}\ldots{}\,v_{i-1} \right\}.$

- [[Countable Set and Uncountable Set]]
- [[Tree-Order Relation]]
- [[Topological Sorting]]


>[!important] Corollary
>A **connected** graph with $n$ vertices is a **tree** *if and only if* it **has $n-1$ edges**.

>[!important] Corollary
>If $T$ is a **tree** and $G$ is any graph with $$\delta(G) \ge |T| - 1,$$ then $$T \subseteq G$$ i.e. $G$ has a *subgraph* **isomorphic** to $T.$

- [[Degree of Vertex]]
- [[Graph Isomorphism]]


-----------
##  Recommended Notes and References


- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]

- [[Graph Operations and Subgraph]]
- [[Paths in Graph and Length of Path]]
- [[Connectivity of Graph]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 13
- [[Networks by Newman]] pp 121 - 123