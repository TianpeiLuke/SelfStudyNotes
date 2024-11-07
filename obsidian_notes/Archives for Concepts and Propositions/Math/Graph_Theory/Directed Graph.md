---
tags:
  - concept
  - math/graph_theory
keywords:
  - directed_graph
topics:
  - math/graph_theory
name: Directed Graph
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Directed Graph

>[!important] Definition
>A **directed graph**  or **digraph** is a pair $(\mathcal{V}, \mathcal{E})$ of disjoint sets (of *vertices* and *edges*) together with two maps
>- $$\text{init}: E \to V \implies e \mapsto \text{int}(e)$$ that assigns every edge $e$ an **initial vertex** $\text{init}(e)$; and
>- $$\text{ter}: E \to V \implies e \mapsto \text{ter}(e)$$ that assigns every edge $e$ an **terminal vertex** $\text{ter}(e)$.


>[!important] Definition
>The edge $e$ in directed graph is said to be **directed** *from* $\text{init}(e)$ to $\text{ter}(e).$
>- There may be multiple edges from same two vertices. Such edges are called **multiple edges**.
>- If multiple edges are of the *same direction*, they are **parallel**. 
>- If $\text{init}(e) = \text{ter}(e)$, the edge $e$ is called a **loop**.



## Explanation





-----------
##  Recommended Notes and References


- [[Directed Acyclic Graph]]
- [[Graph]]

- [[Graph Theory by Diestel]] pp 27
- [[Networks by Newman]] pp 110 - 114