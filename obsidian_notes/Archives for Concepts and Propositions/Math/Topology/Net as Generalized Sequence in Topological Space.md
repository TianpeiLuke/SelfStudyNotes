---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - net_order_sequence
topics:
  - topology
name: Net as Generalized Sequence in Topological Space
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Net as Generalized Sequence in Topological Space

>[!important] Definition
>A **net** in a *topological space* $X$ is a mapping from a **directed system** $I$ to $X$; 
>$$
>I \to X: \alpha \mapsto x_{\alpha}
>$$
>we denote it by $$\set{x_\alpha}_{\alpha \in I}.$$

- [[Directed System of Index Set]]
- [[Topology of Set]]
- [[J Tuples]]
- [[Indexed Family of Sets]]

## Explanation

>[!important]
>**Net** is a *generalization and abstraction* of **sequence**. 
>
>- The directed system $I$ is **not necessarily countable**. So $$\set{x_\alpha}_{\alpha \in I}$$ may *not be a countable sequence.* 
>
>- A **sequence** is a **net** with *countable index set* $I \subseteq \mathbb{N}$. 
>- The directed system can be any set e.g. a *graph*.

- [[J Tuples]]
- [[omega Tuples]]


## Property

>[!important] Proposition
>A point $x$ in a topological space $X$ is a **cluster point** of a **net** $\set{x_\alpha}_{\alpha \in I}$ *if and only if* some **subnet** of $\set{x_\alpha}_{\alpha \in I}$ **converges to** $x$.

- [[Subnet as Generalized Subsequence in Topological Space]]
- [[Convergence of Net and Limit Point and Cluster Point]]





-----------
##  Recommended Notes and References

- [[Directed System of Index Set]]
- [[Topology of Set]]
- [[Indexed Family of Sets]]


- [[Functional Analysis by Reed]]
- [[Topology Book by Munkres]]