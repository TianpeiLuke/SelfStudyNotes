---
tags:
  - concept
  - math/topology
  - topology
  - open_set
  - closed_set
keywords:
  - topology
topics:
  - topology
name: topology
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Topology

>[!important] Definition
> Let $\mathcal{X}$ be a set. A ***topology*** on $\mathcal{X}$ is *a collection* $\mathscr{T}$ of *subsets* of X, called **open subsets**, satisfying
> 1. $X$ and $\emptyset$ are *open*.
> 2. The **union** of **any** *family* of *open subsets* is *open*, i.e. for **any** *sub-collection* of subsets $\mathscr{C} \subset \mathscr{T}$, 
>$$
>\bigcup_{U \in \mathscr{C}}U \in \mathscr{T}
>$$    
> 3. The **intersection** of *any **finite** family* of *open subsets* is *open*, i.e. for any **finite** *sub-collection* of subsets $\mathscr{F} \subset \mathscr{T}$, $\lvert \mathscr{F} \rvert < \infty$,
>$$
>\bigcap_{U \in \mathscr{F}}U \in \mathscr{T}
>$$   
> 
> A pair $(X, \mathscr{T})$ consisting of a set $\mathcal{X}$ together with a topology $\mathscr{T}$ on $\mathcal{X}$ is called a ***topological space***.

- [[Indexed Family of Sets]]
- [[Countable Set and Uncountable Set]]
- [[Set Operations]]



>[!important] Definition
>A subset $A$ of a topological space $X$ is said to be **closed** if the set $X \setminus A$ is *open*.



## Explanation





-----------
##  Recommended Notes and References

- [[Set Operations]]

- Github Note: [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/topology)