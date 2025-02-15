---
tags:
  - concept
  - math/topology
keywords:
  - quotient_topology
topics:
  - topology
name: Quotient Topology
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Quotient Topology

>[!important] Definition
>Let $X$ be a space and $A$ be a set and $\pi: X \rightarrow A$ be a *surjective* map, 
>
>Then there exists **exactly one topology** $\mathscr{T}$ on $A$ relative to which $\pi$ is **quotient map**; it is called **the quotient topology** *induced by* $\pi$. 
>
>**The quotient topology** $\mathscr{T}$ on $A$ is defined as
>$$
> \begin{align*}
> \mathscr{T} = \set{U \subset A:  \pi^{-1}(U) \text{\emph{ is open in }} X}
> \end{align*}
>$$ 

- [[Quotient Map]]
- [[Topology of Set]]


## Explanation


>[!important] 
>The **quotient topology** on a *quotient set* $X / \sim$  is the *weak topology* generated by the *projection map* $\pi: X \to X/\sim$ 
>$$
>\pi: x \mapsto [x], \quad x\in X.
>$$







-----------
##  Recommended Notes and References

- [[Quotient Set]]
- [[Topology of Set]]
- [[Topology Book by Munkres]]