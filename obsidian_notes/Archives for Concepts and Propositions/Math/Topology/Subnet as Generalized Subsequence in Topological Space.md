---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - subset_order_subsequence
topics:
  - topology
  - functional_analysis
name: Subnet as Generalized Subsequence in Topological Space
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Subnet as Generalized Subsequence in Topological Space

>[!important] Definition
>A net  $\set{x_\alpha}_{\alpha \in I}$ is a **subnet** of a *net* $\set{y_\beta}_{\beta \in J}$ *if and only if* there is a *function* $$F: I \rightarrow J$$ such that
>
>- For each $\alpha \in I$,  $$x_\alpha = y_{F(\alpha)}$$
>- For any $\beta' \in J$, there is an $\alpha' \in I$ such that $$\alpha \succ \alpha' \; \implies \; F(\alpha) \succ \beta'$$ 
>  that is, $F(\alpha)$ is **eventually larger** than *any fixed* $\beta \in J$

- [[Net as Generalized Sequence in Topological Space]]
- [[J Tuples]]
- [[Indexed Family of Sets]]

>[!info]
>Equivalent definition
>- $$i \succeq j \implies F(i) \succeq F(j)$$
>- $F(I)$ is **cofinal** in $J.$

- [[Cofinal Subset of Index Set]]


## Explanation





-----------
##  Recommended Notes and References


- [[Strict Partial Order Relation]]
- [[The Maximum Principle]]

- [[Functional Analysis by Reed]]
- [[Topology Book by Munkres]]