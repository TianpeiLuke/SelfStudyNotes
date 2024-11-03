---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_embedding
topics:
  - differential_geometry
name: Smooth Embedding
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Smooth Embedding

>[!important] Definition
>If $M$ and $N$ are smooth manifolds with or without boundary, a **smooth embedding** of $M$ into $N$ is 
>- a *smooth immersion* $F: M \rightarrow N$ that is *also* 
>- a **topological embedding**, i.e., a *homeomorphism* onto its image $F(M) \subseteq N$ in the **subspace topology**. 

^2f0f85

- [[Smooth Immersion]]
- [[Canonical Inclusion]]
- [[Homeomorphism]]
- [[Subspace Topology]]


## Explanation

>[!important]
>From this definition, we see that an **embedding** is 
>- a *topological equivalence* between the domain $M$ and the image $F(M)$, and 
>- it *preserve* the **uniqueness** of *the tangent vectors*.

>[!info]
>A **smooth embedding** is not just a *topological embedding that happens to be smooth*. 

>[!important]
>$F$ is **Smooth Embedding** if:
>- $dF_{p}$ **injective** for all $p$, i.e. $F$ is a **smooth immersion**
>- $\hat{F}: M \to F(M)$ is bijective, i.e. $F$ is **injective**.
>- $\hat{F}$ and $\hat{F}^{-1}$ are **continuous** relative to **subspace topology** of $F(M)$

- [[Subspace Topology]]

>[!info]
>Also a map is a **smooth embedding** $\Rightarrow$ the map is an **injective smooth immersion**. 
>
>The *converse* is *not necessarily true* since this map also need to have **continuous inverse** from $F(M)$ to domain $M$.

## Examples

>[!example]
>If $M$ is a smooth manifold with or without boundary and $U \subseteq M$ is an *open submanifold*, the **inclusion map** $$U \xhookrightarrow{} M$$ is a **smooth embedding**.

- [[Canonical Inclusion]]

>[!example]
>If $M_1,\ldots,M_k$ are smooth manifolds and $p_i \in M_i$ are arbitrarily chosen points, each of the maps $\iota_{j}: M_j \rightarrow M_1\times \ldots \times M_k$ given by
>$$
> \begin{align*}
> \iota_{j}(q) &= \left( p_1, \ldots, p_{j-1}, q, p_{j+1}, \ldots, p_{k} \right)
> \end{align*}
>$$  
>is a **smooth embedding**. 
>
>In particular, the **inclusion map** $$\mathbb{R}^n \xhookrightarrow{} \mathbb{R}^{n+k}$$ given by sending $(x^1,\ldots,x^n)$ to $(x^1,\ldots,x^n, 0,\ldots, 0)$  is a **smooth embedding**.

- [[Canonical Inclusion]]

>[!example]
>The smooth map $X: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ given by
>$$
> \begin{align*}
> X(u,v) =  ((2+ \cos(2\pi u))\cos(2\pi v)\;,\; (2+\cos(2\pi u))\sin(2\pi v)\;,\;\sin(2\pi u))
> \end{align*} 
>$$ 
>descends to a **smooth embedding** of the **torus** $\mathbb{S}^1\times \mathbb{S}^1$ into $\mathbb{S}^3$.

## Properties

>[!important] Criterion for Smooth Embeddings
>Suppose $M$ and $N$ are smooth manifolds with or without boundary, and $F: M \rightarrow N$ is an **injective smooth immersion**. 
>
>If **any** of the following *holds*, then $F$ is a **smooth embedding**.
> 
> - $F$ is an **open** or **closed** map. (i.e. it maps an open/closed set to an open/closed set)
> - $F$ is a **proper map**. (i.e. the preimage of every *compact* set is *compact*)
> - $M$ is **compact**.
> - $M$ has *empty boundary* and $\text{dim }M = \text{dim }N$

- [[Open Map]]
- [[Closed Map]]
- [[Compactness]]




-----------
##  Recommended Notes and References

- [[Smooth Immersion]]

- [[Introduction to Smooth Manifolds by Lee]]