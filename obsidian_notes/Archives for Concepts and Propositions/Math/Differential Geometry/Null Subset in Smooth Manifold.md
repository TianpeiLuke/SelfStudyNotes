---
tags:
  - concept
  - math/differential_geometry
  - math/topology
  - math/measure_theory
keywords:
  - null_set
  - null_subset
topics:
  - measure_theory
  - topology
  - differential_geometry
name: Null Subset in Smooth Manifold
date of note: 2024-05-20
---

## Concept Definitions

>[!important]
>**Name**: Null Subset in Smooth Manifold


>[!important] Definition
>Let $M$ be a smooth $n$-manifold with or without boundary. 
>
>A subset $A \subseteq M$ has **measure zero** in $M$ if for *every smooth chart* $(U, \varphi)$ for $M$, the **subset** $$\varphi(A \cap U ) \subseteq  \mathbb{R}^n$$ has **$n$-dimensional measure zero**. 

- [[Null Subset in Euclidean Space]]
- [[Lebesgue Measure]]

## Criterion for Null Set in Manifold

>[!info]
>The following lemma shows that we need only check this condition for **a single collection of smooth charts** whose *domains cover* $A$. 

>[!important] Lemma
>Let $M$ be a smooth $n$-manifold with or without boundary and $A \subseteq M$. Suppose that for **some collection** $\set{(U_{\alpha}, \varphi_{\alpha})}$ of **smooth charts** whose **domains cover** $A$,  $$\varphi_{\alpha}(A \cap U_{\alpha})$$ has **measure zero** in $\mathbb{R}^n$ for *each* $\alpha$. 
>
>Then $A$ has **measure zero** in $M$.

- [[Smooth Chart and Smooth Coordinate Map]]
## Property of Null Subset in Manifold

>[!important] Proposition
>Suppose $M$ is a smooth manifold with or without boundary and $A \subseteq M$ has **measure zero** in $M$. 
>
>Then $M \setminus A$ is **dense** in $M$.

- [[Dense Set]]

## Smooth Map of Null Set in Manifold

>[!important] Theorem
>Suppose $M$ and $N$ are smooth $n$-manifolds with or without boundary, $F: M \rightarrow N$ is a **smooth map**, and $A \subseteq M$ is a subset of **measure zero**.
>
 >Then $F(A)$ has **measure zero** in $N$.

- [[Smooth Map]]





-----------
##  Recommended Notes and References

- [[Null Subset in Euclidean Space]]
- [[Lebesgue Measure]]


- [[Introduction to Measure Theory by Tao]]
- [[Introduction to Smooth Manifolds by Lee]]