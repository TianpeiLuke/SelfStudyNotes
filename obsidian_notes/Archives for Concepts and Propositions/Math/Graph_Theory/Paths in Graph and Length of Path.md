---
tags:
  - concept
  - math/graph_theory
keywords:
  - path_graph
  - length_path_graph
topics:
  - math/graph_theory
name: Paths in Graph and Length of Path
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Paths in Graph and Length of Path

![[Graph#^40a0c6]]


>[!important] Definition
>A **path** is a non-empty graph $P= (V, E)$ of the form
>$$
>V =\{ x_{0}, x_{1} \,{,}\ldots{,}\, x_{k} \}, \quad E = \{ x_{0}x_{1},\, x_{1}x_{2}, \,{,}\ldots{,}\,  x_{k-1}x_{k}\}
>$$
>where the $x_{i}$ are all *distinct*.
>- The vertices $x_{0}$ and $x_{k}$ are said to be **linked** by $P$, and they are called the **end-vertices** or **ends**
>- The vertices $x_{i}$ for $1 \le i \le k-1$ are the **inner vertices** of $P$.
>- We often refer to a path by the *natural sequence of its vertices*, writing as $$P := x_{0}x_{1}\ldots x_{k}$$ We call $P$ a **path from $x_{0}$ to $x_{k}$**, or **between  $x_{0}$ and $x_{k}$.**
>- Denote a *sub-path* *ends* at $x_{i}$ as $$Px_{i} := x_{0}x_{1}\ldots x_{i}$$
>- Denote a *sub-path* *begins* from $x_{i}$ as $$x_{i}P := x_{i}x_{i+1}\ldots x_{k}$$
>- Denote a *sub-path* *begins* from $x_{i}$ and *end* from $x_{j}$ as $$x_{i}Px_{j} := x_{i}x_{i+1}\ldots x_{j}$$
>- Denote the *interior sub-path* as $$\mathring{P} := x_{1}\ldots x_{k-1}$$
>- Denote the *interior sub-path* of $Px_{i}$ as $$P\mathring{x}_{i} := x_{0}x_{1}\ldots x_{i-1}$$
>- Denote the *interior sub-path* of $x_{i}P$ as $$\mathring{x}_{i}P := x_{i+1}x_{i+2}\ldots x_{k}$$
>- Denote the *interior sub-path* of $x_{i}Px_{j}$ as $$\mathring{x}_{i}P\mathring{x}_{j} := x_{i+1}x_{i+2}\ldots x_{j-1}$$

^a0a3e2


>[!important] Definition
>The *number of edges* in a path is its **length**.
>
>A path of length $k$ is denoted by $P^k$.

>[!important] Definition
>Let $A$ and $B$ be two sets of vertices. 
>
>We call $P = x_{0}x_{1}\,{}\ldots{}\,x_{k}$ an **$A$-$B$ path** if 
>- $$V(P) \cap A = \{ x_{0} \}$$
>- $$V(P) \cap B = \{ x_{k} \}$$

^4b5a59

>[!important] Definition
>Given a graph $H$, we call $P$ an **$H$-path** if 
>- $P$ is *non-trivial*;
>- $P$ meets $H$ exactly in its *ends*.

>[!info]
>The edge of $H$-path of *length* $1$ is never an edge of $H$.

## Explanation


>[!info]
>Suppose of $P$ and $Q$ join at $y$, we can define a path $$xPyQz$$ that starts at $x$ and traverse along path $P$ to $y$ and then from $y$ traverse along path $Q$ to $z$. 




-----------
##  Recommended Notes and References

- [[Cycles in Graph]]
- [[Walk and Trail in Graph]]
- [[Graph Operations and Subgraph]]
- [[Graph]]

- [[Interior of Set]]

- [[Graph Theory by Diestel]] pp 6
- Wikipedia [Path_(graph_theory)](https://en.wikipedia.org/wiki/Path_(graph_theory))