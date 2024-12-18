---
tags:
  - concept
  - math/topology
keywords:
  - sub-basis
  - topology_generated_by_subbasis
topics:
  - topology
name: sub-basis of topology
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Sub-Basis of Topology


>[!important] Definition
>A **subbasis** $\mathscr{B}$ for a *topology* on $X$ is a collection of subsets of $X$ whose **union** equals $X$. 
>
>Formally, let $X$ be a topological space with topology $\mathscr{T}$. A **subbase** of $\mathscr{T}$ is usually defined as *a subcollection*  $\mathscr{B}$ of $\mathscr{T}$ satisfying *one* of the two following *equivalent conditions*:
> - The subcollection $\mathscr{B}$  _generates_ the topology $\mathscr{T}$. 
> 	- This means that $\mathscr{T}$ is **the smallest topology** *containing* $\mathscr{B}$: any topology $\mathscr{T}^{'}$ on $X$ containing $\mathscr{B}$ must also contain $\mathscr{T}$.
> - The collection of *open sets* consisting of *all finite intersections* of elements of $\mathscr{B}$, together with the set $X$ forms a basis for $\mathscr{T}$. 
> 	- This means that every proper *open set* in $\mathscr{T}$ can be written as a **union of finite intersections** of elements of $\mathscr{B}$. 
>

>[!info]
>Explicitly, given a point $x\in X$ in an *open set* $U \subseteq X$, there are *finitely many* sets $S_1, \ldots, S_n$ of $\mathscr{B},$ such that *the intersection of these sets* contains $x$ and *is contained* in $U$.
>
>i.e. for any $x\in X$ and any open set $U \in \mathscr{T}$, there exists some $n <\infty$ and  $\{S_i\}_{i=1}^{n} \subset \mathscr{B}$ such that
> $$
> \begin{align*}
> x \in \bigcap_{i=1}^{n}S_i \\
> \bigcap_{i=1}^{n}S_i \subseteq U&
> \end{align*}
> $$


>[!important] Definition
>**The topology generated by the _subbasis_ $\mathscr{B}$** is defined to be the collection $\mathscr{T}$ of *all **unions of finite intersections** of elements* of $\mathscr{B}$.
>$$
>\mathscr{T} = \bigcup_{n \text{ finite}}\left\{ \bigcap_{i=1}^{n}S_i, \; S_1, \ldots, S_n \in \mathscr{B} \right\}
>$$






## Explanation





-----------
##  Recommended Notes and References

- [[Topology of Set]]
- [[Basis of Topology]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)