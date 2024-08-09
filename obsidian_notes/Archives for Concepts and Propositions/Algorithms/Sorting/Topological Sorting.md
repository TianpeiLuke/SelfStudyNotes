---
tags:
  - concept
  - algorithm/graph
  - algorithm/sort
keywords:
  - topological_order_graph
  - topological_sorting
topics:
  - algorithm/sort
  - algorithm/graph
name: Topological Sorting
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Topological Sorting


>[!important] Definition
>The **Kahn's algorithm** for topological sort algorithm on a graph $G = (V,E)$ is described as below
>- *Require*: graph $G = (V, E)$
>- *Initialization*: $L \leftarrow$ Empty list that will contain the sorted elements
>- *Initialization*: $S \leftarrow$  Set of all nodes with *no incoming edge*
> 
>- while $S$ is not empty:
>	- **remove** a node $n$ from $S$
>	- *add* $n$ to $L$
>	- for each node $m$ with **an edge** $e$ *from* $n$ *to* $m$:
>		- **remove edge** $e$ from the graph
>		- if $m$ has **no other incoming edges**:
>			- *insert* $m$ into $S$
> 
>- if _graph_ has edges:
>	- **return** error   _(graph has at least one cycle)_
>- else 
>	- **return** _L_   _(a topologically sorted order)_


## Explanation





-----------
##  Recommended Notes and References


- [[Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 1144