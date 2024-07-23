---
tags:
  - concept
  - math/graph_theory
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
keywords:
  - hypergraph_graph_theory
topics:
  - math/graph_theory
name: Hypergraph
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Hypergraph in Graph Theory

>[!important] 
>A **hypergraph** is a generalization of graph in which an edge can join *any number of vertices*.

>[!important] Definition
>A **hypergraph** is a pair $(V, E)$ of disjoint sets, where the elements of $E$ are *non-empty subsets* (of any cardinality) of $V$. 
>
>- $V$ is a set of *elements*, *vertices*, or *nodes*.
>- Each pair $(D, C) \in E$ where $C, D \subseteq V$ is called an *edge* or **hyperedge**;
>- For a *directed edge* $(D, C)\in E$, 
>	- the vertex subset $D$ is called its **tail** or **domain**.
>	- the vertex subset $C$ is called its **head** or **codomain**
>	- we can represent the directed edge as $$e: D\to C$$

- [[Directed Graph]]
- [[Graph]]


>[!info]
>A **graph** is a special case of *hypergraph*.

>[!important] Definition
>- The **order** of a *hypergraph* $(V,E)$ is the *number of vertices* in $V$, $|V|$.
>- The **size** of a *hypergraph* $(V,E)$ is the *number of edges* in $E$, $|E|$.
>- The **order** of an *edge* or *hyperedge* $e:= (D,C)$  is the tuple $$|e| := (|D|, |C|).$$ that is, the number of *vertices* in its *tail* followed by the number of vertices in its head.

>[!info]
>The hypergraph can be used to model functional relationship between sets.



## Explanation





-----------
##  Recommended Notes and References

- [[Cluster Graph and Family Preservation]]
- [[Graph]]
- [[Set Operations]]

- [[Graph Theory by Diestel]] pp 27
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 260
- Wikipedia [Hypergraph](https://en.wikipedia.org/wiki/Hypergraph)