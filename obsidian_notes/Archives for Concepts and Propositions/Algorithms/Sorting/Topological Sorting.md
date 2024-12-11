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
>- while $S \neq \emptyset$:
>	- **remove** a node $n$ from $S$ $$S \leftarrow S \setminus \{ n \}$$
>	- *add* $n$ to $L$  $$L \leftarrow L \cup \{ n \}$$
>	- for each node $m$ with **an edge** $e$ *from* $n$ *to* $m$, i.e. $m\in \text{Ch}(n)$:
>		- **remove edge** $e$ from the graph $$E \leftarrow E \setminus \{ e \}, \quad \text{Ch}(n) \leftarrow \text{Ch}(n) \setminus \{ m \}$$
>		- if $m$ has **no other incoming edges**, i.e. $\text{Pa}(m) = \emptyset$:
>			- *insert* $m$ into $S$ $$S \leftarrow S \cup \{ m \}$$
> 
>- if _graph_ has edges:
>	- **return** error   _(graph has at least one cycle)_
>- else 
>	- **return** _L_   _(a topologically sorted order)_

- [[Oriented Directed Graph]]
- [[Directed Graph]]


## Explanation


## Topological Sort in Optimization and Machine Learning

### Automatic Differentiation

- [[Automatic Differentiation]]
- [[Back-Propagation Algorithm]]

### Graphical Model

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Expectation Propagation Algorithm]]
- [[Max-Product Belief Propagation for Clique Tree]]
- [[Max-Product Belief Update for Clique Tree]]



-----------
##  Recommended Notes and References


- [[Graph]]
- [[Algorithm General Definition]]
- [[Data Structure General Definition]]

- [[Introduction to Algorithms by Cormen]] pp 573 - 576
- [[Algorithm Design Manual by Skiena]] pp 546 - 549
- [[Probabilistic Graphical Models by Koller]] pp 1144