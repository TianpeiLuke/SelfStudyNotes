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
name: Null Subset in Euclidean Space
date of note: 2024-05-20
---

## Concept Definitions

>[!important]
>**Name**: Null Subset in Euclidean Space


>[!important] Definition
>A set $A \subseteq \mathbb{R}^n$ to have **measure zero** if 
>
>for any $\delta > 0$,  $A$ can be *covered* by *a countable collection* of *open* rectangles, the **sum** of whose **volumes** is *less than* $\delta$.

- [[Lebesgue Measure]]
- [[Positive Set Negative Set Null Set]]

## Measure Zero Sets

### Compact Subset with Measure Zero Slice

>[!important] Lemma
>Suppose $A \subseteq \mathbb{R}^n$ is a **compact subset** whose *intersection* with $$\set{c} \times \mathbb{R}^{n-1}$$ has  $(n-1)$-dimensional **measure zero** for **every** $c \in \mathbb{R}$. 
>
>Then $A$ has **$n$-dimensional measure zero**.

- [[Fubini Theorem]]
- [[Compactness]]
- [[Linear Subspace]]

### Graph of Continuous Function with Open or Closed Domain

>[!important] Proposition
>Suppose $A$ is an **open or closed** subset of $\mathbb{R}^{n-1}$ or $\mathbb{H}^{n-1}$, and $$f: A \rightarrow \mathbb{R}$$ is a **continuous function**. 
>
>Then the **graph** of $f$ 
>$$
>\Gamma(f) := \left\{(x, f(x)): x\in A  \right\}
>$$
>has **measure zero** in $\mathbb{R}^n$.

- [[Continuous Function]]

>[!important] Corollary
>Every **proper affine subspace** of $\mathbb{R}^n$ has **measure zero** in $\mathbb{R}^n$.

- [[Affine Hull]]

### Smooth Map of Null Set in Euclidean Space

>[!important] Proposition
>Suppose $A \subseteq \mathbb{R}^n$ has **measure zero** and $F: A \rightarrow \mathbb{R}^n$ is a **smooth** map. 
>
>Then $F(A)$ has **measure zero.**

- [[Smooth Map between Euclidean Spaces]]




-----------
##  Recommended Notes and References

- [[Lebesgue Measure]]
- [[Positive Set Negative Set Null Set]]


- [[Introduction to Measure Theory by Tao]]
- [[Introduction to Smooth Manifolds by Lee]]