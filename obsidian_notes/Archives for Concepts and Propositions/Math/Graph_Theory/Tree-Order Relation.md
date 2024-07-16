---
tags:
  - concept
  - math/graph_theory
keywords:
  - rooted_tree
  - root_graph
topics:
  - math/graph_theory
name: Tree-Order
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Tree-Order

![[Tree Graph and Forest#^90f857]]

![[Strict Partial Order Relation#^426824]]

>[!important] Definition
>Let $T$ be a *rooted tree* with *root* $r$. Define a relation $\leq$ on $V(T)$ as 
>$$
>x \leq y \iff x \in rTy
>$$
>That is $x \le y$ if and only if $x$ is *on the path* from $r \to y$, or $x$ is the **ancestor** of $y$.
>
>We can show that $\le$ is a *partial order relation*, called the **tree-order** *associated with* $T$ and $r$.

- [[Root and Rooted Tree]]
- [[Strict Partial Order Relation]]

>[!info]
>If $x < y$, then $x$ **lies below** $y$ in $T$

>[!important] Definition
>Let $x, y \in V(T)$ .
>
>
>- The **down-closure** of $y$ is defined as $$\lceil y  \rceil := \left\{ x \in V(T): x \le y \right\} $$
>- The **up-closure** of $x$ is defined as $$\lfloor x \rfloor := \left\{ y \in V(T): y \ge x \right\}  $$

>[!important] Definition
>A set $X \subset V(T)$ is called **closed upwards**, or **up-closed**, or an **up-set** in $T$ if it equals its *up-closure*, i.e. $$X = \lfloor X \rfloor = \bigcup_{x\in X}\lfloor x \rfloor  $$
>
>A set $Y\subset V(T)$ is called **closed downwards**, or **down-closed**, or an **down-set** in $T$ if it equals its *down-closure*, i.e. $$Y = \lceil Y \rceil = \bigcup_{y\in Y} \lceil y \rceil  $$

>[!important] Definition
>A *rooted tree* $T$ contained in a graph $G$ is called **normal** in $G$ if the *ends* of every *$T$-path* in $G$ are *comparable* whenever they are *adjacent* in $G$.



## Explanation

>[!important]
>Note that 
>- the **root** of $T$ is the **least element** in its *tree-order*, 
>- the **leaves** are its *maximal elements*, 
>- the **ends** of *any edge* of T are **comparable**, and 
>- the **down-closure** of *every vertex* is a **chain**,  a set of *pairwise comparable elements*.




-----------
##  Recommended Notes and References


- [[Strict Partial Order Relation]]

- [[Tree Graph and Forest]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 15