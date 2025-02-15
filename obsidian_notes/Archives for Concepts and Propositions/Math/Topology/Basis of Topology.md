---
tags:
  - concept
  - math/topology
keywords:
  - basis
  - topology
topics:
  - topology
name: basis of topology
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Basis of Topology


>[!important] Definition
>Suppose $X$ is a topological space. A collection $\mathscr{B}$ of open subsets of $X$ is said to be a **basis** for *the topology of $X$* (plural: **bases**) if *every open* subset of $X$ is the *union of some collection of elements* of $\mathscr{B}$.

>[!important] Definition
More generally, suppose $X$ is merely a set, and $\mathscr{B}$ is a *collection of subsets* of $X$ satisfying the following conditions:
> 1. $$X = \bigcup_{B \in \mathscr{B}}B.$$
> 2. If $B_1, B_2 \in \mathscr{B}$ and $x \in B_1 \cap B_2$, then there exists $B_3 \in \mathscr{B}$ such that $$x \in B_3 \subseteq B_1 \cap B_{2}.$$
> 
> Then _the collection of **all unions** of elements of $\mathscr{B}$_ is a *topology* $\mathscr{T}$ on X, called **the topology $\mathscr{T}$ generated by $\mathscr{B}$**, and $\mathscr{B}$ is a **basis** for this *topology*.




## Explanation





-----------
##  Recommended Notes and References

- [[Topology of Set]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)