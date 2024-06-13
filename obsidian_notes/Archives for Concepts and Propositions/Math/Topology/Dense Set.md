---
tags:
  - concept
  - math/topology
keywords:
  - dense_set
topics:
  - topology
name: Dense Set
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Dense Set


>[!important] Definition
>A subset $A$ of a topological space $X$ is said to be **dense** *in $X$* if every point of $X$ either belongs to $A$ or is a *limit point* of $A$

- [[Limit Point]]

>[!important] Equivalent Definitions
>A subset $A$ of a topological space $X$ is said to be a **dense subset of $X$** if any of the following equivalent conditions are satisfied:
> - The **smallest closed** subset of $X$ **containing $A$** is $X$ itself.
> - The **closure** of $A$ in $X$ is equal to $X$. That is, $$\text{cls}(A) = X.$$
> - The **interior** of the *complement* of $A$ in $X$ is empty. That is, $$\text{int}_{X}(A^{c}) = \emptyset.$$
> - Every point in $X$ either *belongs to* $A$ or is **a limit point** of $A$
> - For every $x \in X$, *every neighborhood* $U$ of $x$ *intersects* $A$; that is, $$U \,\cap \, A \neq \emptyset.$$
> - $A$ *intersects* every non-empty open subset of $X$ 
> - If $\mathscr{B}$ is a **basis** for the topology of $X$, then for every $x \in X$, every *basis neighborhood* $B \in \mathscr{B}$ of $x$ *intersects* $A$
> - $A$ intersects *every non-empty basis* element $B \in \mathscr{B}$

- [[Topology of Set]]
- [[Closure of Set]]
- [[Interior of Set]]
- [[Basis of Topology]]


## Explanation





-----------
##  Recommended Notes and References

- Wikipedia [Dense set](https://en.wikipedia.org/wiki/Dense_set)
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)