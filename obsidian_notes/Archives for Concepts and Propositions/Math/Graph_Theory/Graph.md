---
tags:
  - concept
  - math/graph_theory
keywords:
  - graph
topics:
  - math/graph_theory
name: Graph
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Graph

>[!important] Definition
>A **graph** $\mathcal{G}$ is a pair of sets $(\mathcal{V}, \mathcal{E})$, where $$\mathcal{E} \subset \mathcal{V} \times \mathcal{V}$$
>- The elements of $\mathcal{V}$ are called the **vertices** (or **nodes**,or **points**) of the graph $\mathcal{G}$;
>- The elements of $\mathcal{E}$ are its **vertex edges** (or **lines**.)

- [[Set Operations]]

>[!important] Definition
>- A graph with vertex set $\mathcal{V}$ is called a **graph on $\mathcal{V}$**, denoted as $G(\mathcal{V})$
>- The **vertex set of a graph** $\mathcal{G}$ is denoted as $V(\mathcal{G})$; 
>- The **edge set of a graph** $\mathcal{G}$ is denoted as $E(\mathcal{G})$
>- The *number of vertices* of a graph $\mathcal{G}$ is its **order**, written as $|\mathcal{G}|$.
>	- Graphs are **finite**, **infinite**, **countable** and so on according to their order.
>	- We write **empty graph** $(\emptyset, \emptyset)$ as $\emptyset$
>	- A graph of order $0$ and $1$ is called a **trivial graph**.

>[!important] Definition
>- A vertex $v$ is **incident with an edge** $e$ if $v \in e$; 
>	- then $e$ is an **edge at** $v$.
>- The two vertices *incident with an edge* are its **end vertices** or **ends**, and an *edge* **joins** its *ends*.

>[!important] Definition
>An edge $(u, v)$ is usually written as $uv$.
>
>If $u\in \mathcal{X}$ and $v\in \mathcal{Y}$, then the edge $uv$ is a **$\mathcal{X}$-$\mathcal{Y}$ edge**.
>
>The **set of all** $\mathcal{X}$-$\mathcal{Y}$ edges is denoted as $E(\mathcal{X}, \mathcal{Y}).$
>- The set  of all edges *starting from a common end* $x$ to set $\mathcal{Y}$ is denoted as $E(x, \mathcal{Y})$
>- The set of all edges from $\mathcal{X}$ *to a common end* $y$ is denoted as $E(\mathcal{X}, y)$
>- The set of all edges in $\mathcal{E}$ *at a vertex* $v$ is denoted as $E(v)$

^40a0c6

- [[Graph Theory by Diestel]] pp 2

>[!important] Definition
>Two vertices $x,y$ of $G$ are **adjacent**, or **neighbors**, if $\{ x,y \}$ is an *edge* in $G$.
>
>Two edges $e\neq f$ are **adjacent** if they have an *end* in common.



## Explanation

>[!important]
>A graph $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ is 
>- a **visual representation** of **elements** in the set $\mathcal{V}$ and their **pairwise relation** in $\mathcal{E}$
>- a **data structure** for **entities** and their **dependencies**
>- a **topology** of *sets* which emphasizes the *connectivity*

- [[Relation]]
- [[Topology of Set]]
- Wikipedia [Graph (topology)](https://en.wikipedia.org/wiki/Graph_(topology)#:~:text=In%20topology%2C%20a%20branch%20of,with%20the%20point%20associated%20to)
- Wikipedia [Topological_graph_theory](https://en.wikipedia.org/wiki/Topological_graph_theory)


## Graph as Data Structure and Algorithms

- [[Data Structure General Definition]]
- [[Breadth-First Search]]
- [[Breadth-First Search]]
- [[Best-First Search]]

## Probabilistic Graphical Model

- [[Models and Algorithms for Probabilistic Graphical Models]]



-----------
##  Recommended Notes and References

- [[Directed Acyclic Graph]]
- [[Bipartite Graph]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 34
- [[Graph Theory by Diestel]] pp 2