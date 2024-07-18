---
tags:
  - concept
  - math/graph_theory
keywords:
  - spanning_tree
  - chord_tree
topics:
  - math/graph_theory
name: Spanning Tree and Chord
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Spanning Tree and Chord



![[Spanning Subgraph#^af8197]]

>[!important] Definition
>A tree $T$ is a **spanning tree** of a graph $G=(V,E)$ if 
>- $T \subset\, G$
>- $$V(T) = V(G)$$

- [[Tree Graph and Forest]]
- [[Spanning Subgraph]]

>[!important] Definition
>When $T$ is a *spanning tree* of $G$, the edges $$E(G) \setminus\, E(T)$$ are the **chords** of $T$ in $G$.



## Explanation



## Connected Graph

![[Tree Graph and Forest#^4f77eb]]

- [[Connected Graph and Connected Component of Graph]]

>[!important] 
>A common application of above theorem is that every *connected graph* contains a **spanning tree**.
>- take a *minimal connected spanning subgraph* and use (3), or 
>- take a *maximal acyclic subgraph* and apply (4). 



-----------
##  Recommended Notes and References


- [[Spanning Subgraph]]
- [[Tree Graph and Forest]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 14