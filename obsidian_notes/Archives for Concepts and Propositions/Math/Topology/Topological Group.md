---
tags:
  - concept
  - math/topology
  - math/abstract_algebra
  - math/algebraic_topology
keywords:
  - topological_group
topics:
  - topology
  - algebra
  - algebraic_topology
name: Topological Group
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Topological Group

>[!important] Definition
>A **topological group** $G$ is a *group* that is also a *topological space* satisfying **the $T_1$ axiom**, such that  
>- the **multiplication map** $m: G \times G \rightarrow G$ 
>$$
>m(x, y) = x y
>$$
>- the **inversion map** $i: G \rightarrow G$, given by
>$$
>i(x) = x^{-1.}
>$$  
>
>are both **continuous maps**. 

- [[Group]]
- [[Topology of Set]]
- [[First Countablity]]

>[!info]
>Here, $G\times G$ is viewed as a **topological space** by using **the product topology**.


## Explanation

>[!important] Proposition
>Every **topological group** is a **homogeneous** space; in particular,  define 
>- map $h_{\alpha}: G\to G$ as $$h_{\alpha}(x) = \alpha\cdot x$$ and
>- map $g_{\alpha}: G\to G$ as $$g_{\alpha}(x) = x \cdot \alpha,$$ for $\alpha\in G$.
>  
>Then $h_{\alpha}, \, g_{\alpha}$ are **homemorphisms.**

- [[Homogeneous Space]]
- [[Homeomorphism]]

- [[Left Coset and Right Coset of Group]]


-----------
##  Recommended Notes and References


- [[Topology of Set]]

- [[Topology Book by Munkres]]