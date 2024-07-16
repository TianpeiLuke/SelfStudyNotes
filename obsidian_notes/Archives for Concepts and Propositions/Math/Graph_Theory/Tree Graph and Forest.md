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
>- $T$ is **minimally connected**, i.e. $T$ is *connected*, but $T \setminus \{ e \}$ is *disconnected* for *every edge* $e\in T$.
>- $T$ is **maximally acyclic**, i.e. $T$ contains no *cycle*, but $T \,\cup\, \{ xy \}$ does contain an cycle for any two *non-adjacent vertices* $x, y\in T.$

>[!important] Definition
>Since the path from $x \to y$ in $T$ is unique, we denote the **unique path** *from* $x$ to $y$ as $xTy$.




-----------
##  Recommended Notes and References


- [[Root and Rooted Tree]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 13