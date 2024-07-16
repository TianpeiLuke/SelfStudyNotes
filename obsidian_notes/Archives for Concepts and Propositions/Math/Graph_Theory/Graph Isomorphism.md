---
tags:
  - concept
  - math/graph_theory
keywords:
  - graph_isomorphism
topics:
  - math/graph_theory
name: Graph Isomorphism
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Graph Isomorphism

![[Graph Homomorphism#^bbdef7]]

>[!important] Definition
>Let $G =(V, E)$ and $G' =(V',E')$ be *two graphs*. 
>
>A map $\varphi: V \to V'$ is a **isomorphism** from $G$ to $G'$ if 
>- $\varphi$ is a *homomorphism*, i.e. *preserves the adjacency* of *vertices*, that is, $$( x, y ) \in E \implies ( \varphi(x), \varphi(y) ) \in E'.$$
>- $\varphi$ is **bijective** and 
>- its *inverse* $\varphi^{-1}: V' \to V$ is also a *homomorphism*, i.e. $$(x, y) \in E \iff (\varphi(x), \varphi(y)) \in E', \quad \forall x, y \in V.$$
>  
>We say that $G$ and $G'$ are **isomorphic**, and write $$G \simeq G'.$$  

^09d902

- [[Isomorphism between Groups]]


>[!important] Definition
>An *isomorphism* from $G$ *to itself* is an **automorphism** of $G$.

- [[Automorphism between Groups]]
- [[Symmetric Group]]



## Explanation





-----------
##  Recommended Notes and References


- [[Graph Homomorphism]]
- [[Graph]]

- [[Bijective Function and Inverse Function]]

- [[Homomorphism between Groups]]
- [[Isomorphism between Groups]]
- [[Automorphism between Groups]]


- [[Graph Theory by Diestel]] pp 3