---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - weak_topology
topics:
  - functional_analysis
name: Weak Topology Generated by a Family of Functions
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  $\mathcal{F}$-Weak Topology on Function Space


>[!important] Definition
>Let $\mathcal{F}$ be a *family of functions* from a set $S$ to a *topological vector space* $(X, \mathscr{T})$. 
>
>The **$\mathcal{F}$-weak** (or simply **weak topology**) on $S$ is the *weakest topology* for which *all* the functions $f \in \mathcal{F}$ are **continuous**.



## Explanation

>[!important]
>**The $\mathcal{F}$-weak topology does not arise from a metric**. This is one of the main reasons we have introduced topological spaces.

## Sub-basis

>[!important]
>The **sub-basis** for *weak topology* generated by $\mathcal{F}$ is defined as
>$$
> \begin{align*}
> S(\mathcal{F},U) = \set{f^{-1}(U): f \in \mathcal{F}}.
> \end{align*}
> $$
> where $U \in \mathscr{T}$ is any open subset in $X$.

- [[Preimage and Range of Function]]


## Product Topology

- [[Product Topology]]


-----------
##  Recommended Notes and References

- [[Topological Vector Space]]
- [[Sub-Basis of Topology]]

- [[Topology of Pointwise Convergence]]


- [[Introductory Functional Analysis with Applications by Kreyszig]]
- [[Functional Analysis by Reed]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)

