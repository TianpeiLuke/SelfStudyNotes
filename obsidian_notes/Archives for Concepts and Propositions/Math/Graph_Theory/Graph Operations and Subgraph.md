---
tags:
  - concept
  - math/graph_theory
keywords:
  - subgraph
topics:
  - math/graph_theory
name: Subgraph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Graph Operations and Subgraph

>[!important] Definition
>Let $G' = (V', E')$ and $G = (V, E)$.
>- **Graph Union**: $$G \cup G' := \left(V \cup V' \,,\, E \cup E' \right)$$
>- **Graph Intersection**: $$G \cap G' := \left(V \cap V' \,,\, E \cap E' \right)$$
>- **Graph Difference (Node Deletion)**: $$G - U := G \setminus\, U := G[V \setminus\, U], \quad \forall U \subseteq V$$ That is $G \setminus\, U$ is obtained by **deleting** all *vertices* in $V\cap U$ and all their *induced edges*.
>	- If $V := \left\{ v \right\}$, we write $$G - v := G \setminus\, \{v\}$$
>- **Graph Difference**: $$G - G' = G \setminus\, G' := G \setminus\, V(G')$$
>- **Graph Difference (Edge Deletion)**:  $$G - F := G \setminus\, F := (V, E\setminus\,F), \quad \forall F \subseteq E$$
>	- If $F = \{e\}$, then $$G - e = G \setminus\, \left\{ e \right\}$$
>- **Edge Addition**:  $$G + F := (V, E\cup\,F)$$
>	- If $F = \{e\}$, then $$G + e = G + \left\{ e \right\}$$
>- If $G$ and $G'$ are *disjoint*, we denote $$G * G' := G \cup G' + \left\{xy:\, x\in V(G),\, y \in V(G') \right\}.$$
>- **Graph Complements**: the graph complements is the subgraph that is *complementary to* $G$ with respect to a *complete graph* $$G^{c} = \overline{G} := (V\,,\, (V\times V) \setminus\, E).$$

^69d7e9

- [[Set Operations]]
- [[Complete Graph and Triangle]]


>[!important] Definition
>If $G \cap G' = \emptyset$, then $G$ and $G'$ are **disjoint**.

>[!important] Definition
>Let $G' = (V', E')$ and $G = (V, E)$.
>
>If $$V' \subseteq V \text{ and } E' \subseteq E,$$ then $G'$ is a **subgraph** of $G$ (and $G$ a **supergraph** of $G'$), written as $$G' \subseteq G.$$
>
>Less formally, we say that **$G$ contains $G'$**.

^5e31a1

>[!important] Definition
>If $$G' \subseteq G \text{ and } G' \neq G,$$ then $G'$ is a **proper subgraph** of $G$.





## Explanation





-----------
##  Recommended Notes and References


- [[Minimal and Maximal Property of Graph]]
- [[Graph Property]]
- [[Line Graph]]
- [[Graph]]


- [[Set Operations]]

- [[Graph Theory by Diestel]] pp 3 - 4