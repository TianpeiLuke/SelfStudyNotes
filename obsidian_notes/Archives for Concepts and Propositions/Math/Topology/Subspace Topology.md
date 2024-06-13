---
tags:
  - concept
  - math/topology
keywords:
  - subspace_topology
topics:
  - topology
name: Subspace Topology
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Subspace Topology

>[!important] Definition
>If $(X, \mathscr{T})$ is a *topological space* and $S \subseteq X$ is an arbitrary subset, we define the **subspace topology** on $S$ (sometimes called the **relative topology**) as
>$$
> \begin{align*}
> \mathscr{T}_{S} &= \set{S\cap U: U \in \mathscr{T}}
> \end{align*} 
>$$
> 
> That is, a *subset* $U \subseteq S$ to be **open** in $S$ **if and only if** there exists an **open** subset $V \subseteq X$ such that $$U = V \cap S.$$  

- [[Intersection of Set Family to Set]]

>[!important]
> Any subset of $X$ endowed with *the subspace topology* is said to be a **subspace of $X$**.

>[!important] Lemma (Basis of Subspace Topology)
>If $\mathscr{B}$ is a **basis** for the **topology of** $X$ then the collection
>$$
> \begin{align*}
> \mathscr{B}_{S} = \set{B \cap S:  B \in \mathscr{B}}
> \end{align*}
>$$ 
> is a **basis**  for the **subspace topology** on $S \subset X$.

- [[Basis of Topology]]

## Explanation

>[!important] Open Relative to Subspace Topology or its own Topology
>When dealing with a space $X$ and a **subspace** $Y$, one needs to be careful when one uses the term **"open set"**.
>
> Does one mean *an element of __the topology of $Y$__* or *an element of __the topology of $X$__* ? 
> 
> We make the following definition :
>>[!quote] 
>> - If $Y$ is a subspace of $X$, we say that a set $U$ is **open in** $Y$ (or open **relative to** $Y$}) if it *belongs to the topology of* $Y$; this implies in particular that it is a **subset** of $Y$. 
>>- We say that $U$ is **open in** $X$ if it belongs to *the topology of *$X$.




-----------
##  Recommended Notes and References


- [[Topology of Set]]


- [[Topology Book by Munkres]]