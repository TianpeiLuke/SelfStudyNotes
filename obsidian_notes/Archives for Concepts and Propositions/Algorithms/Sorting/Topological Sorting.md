---
tags:
  - concept
  - algorithm/graph
  - algorithm/sort
keywords: 
topics: 
name: 
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: 


>[!important] Kahn's algorithm
>$L \leftarrow$ Empty list that will contain the sorted elements
>$S \leftarrow$  Set of all nodes with *no incoming edge*
> 
>- while$S$ is not empty:
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