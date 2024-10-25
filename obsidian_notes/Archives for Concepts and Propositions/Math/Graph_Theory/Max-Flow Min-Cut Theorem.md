---
tags:
  - concept
  - math/graph_theory
keywords:
  - graph
  - maximum_flow
  - minimum_cut
topics:
  - math/graph_theory
name: Max-Flow Min-Cut Theorem
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Max-Flow Min-Cut Theorem

![[Network and Flow and Capacity and Cut#^9fa477]]

![[Network and Flow and Capacity and Cut#^4a27b4]]

![[Network and Flow and Capacity and Cut#^667ae1]]

>[!important] Max-Flow Min-Cut Theorem
>In every **network**, the **maximum total value** of a **flow** *equals to* the **minimum capacity** of a **cut**.
>
>That is
>$$
>\max_{f \text{ flow constraints}}\sum_{sy\in E}f(e, s, y) := \max_{f \text{ flow constraints}}\,f(s, V) = \min_{S\subset V, s\in S}c(S, \bar{S})
>$$


- [[Network and Flow and Capacity and Cut]]
- [[Cut Space of Graph]]


## Explanation



## Linear Programming

![[Maximum Flow Problem#^19518d]]

- [[Network Flow Problem as Linear Optimization]]
- [[Maximum Flow Problem]]
- [[Fenchel Duality Theorem]]



-----------
##  Recommended Notes and References



- [[Maximum Flow Problem]]

- [[Graph]]
- [[Graph Theory by Diestel]] pp 153