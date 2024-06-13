---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_submersion
topics:
  - differential_geometry
name: Smooth Submersion
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Smooth Submersion

>[!important] Definition
>A smooth map $F: M \rightarrow N$ is called a **smooth submersion** if its *differential* is *surjective* *at each point*. 
>
>or *equivalently*, if $$\text{rank }F = \text{dim }N.$$


- [[Rank of Smooth Map]]
- [[Differential of a Smooth Map at Point]]
- [[Surjective Function]]
- [[Canonical Projection]]

## Explanation

>[!important] Proposition
>Suppose $F: M \rightarrow N$ is a smooth map and $p \in M$ . 
>
>If $dF_p$ is **surjective**, then $p$ has a *neighborhood* $U$ such that $F|_{U}$ is a **submersion**. 


>[!info]
>A map $F: M \rightarrow N$ is 
>- **surjective** if the preimage $F^{-1}(N)$ *covers* its domain $M$. 
>- **submersion** if its **differential** $dF_p$ at $p$ is **surjective** *for all $p$.* 

>[!important] 
>The concept
>- **submersion/immersion**: about the **local differential property** of $F$ 
>- **surjective/injective**:  about the **global property** of $F$.  
>  
>Local property can *be determined by* the global property but not vice versa. 
>
>Thus a map 
>- can be **submersion** but *may not be surjective*.  
>- can be **immerison** but may *not be injective*. 



## Examples

>[!example]
>Suppose $M_1,\ldots,M_k$ are smooth manifolds. 
>
>Then each of the **canonical projection maps** $$\pi_{i}: M_1\times \ldots \times M_k \rightarrow M_i$$ is a **smooth submersion**. 
>
>In particular, the **projection** $$\pi: \mathbb{R}^{n+k} \rightarrow \mathbb{R}^n$$ **onto** the *first $n$ coordinates* is a **smooth submersion**.

- [[Canonical Projection]]

>[!example]
>If $M$ is a smooth manifold and its *tangent bundle* $TM$ is given the smooth manifold structure described in [[Tangent Bundle]],  the **bundle projection** $$\pi: TM \rightarrow M$$ is a **smooth submersion.** 

>[!info]
>To verify this, just note that with respect to any smooth local coordinates $(x^i)$ on an open subset $U \subseteq M$ and the corresponding *natural coordinates* $(x^i, v_i)$ on  $\pi^{-1}(U) \subseteq TM$, the **coordinate representation** of $\pi$ is $$\widehat{\pi}(x, v) = x.$$

- [[Coordinate Representation of Element in Vector Bundle]]
- [[Vector Bundle]]

## Canonical Representation of Submersion


>[!important]
>By [[Rank Theorem]], the **canonical representation** for a **smooth submersion** 
>$$
>\widehat{F}(x^1,\ldots, x^r, x^{r+1},\ldots, x^m) = (x^1,\ldots, x^r, 0,\ldots, 0).
>$$
 >is called the **canonical surjection** or the **projection map**, denoted as $\pi$;  

- [[Canonical Projection]]

## Local Section Theorem

- [[Section of Continuous Function]]
- [[Local Section Theorem and Smooth Submersion]]

## Property of Smooth Submersion

>[!important] Proposition
>Let $M$ and $N$ be smooth manifolds, and suppose $\pi: M \rightarrow N$ is a *smooth submersion*. 
>
>Then $\pi$ is an **open map**, and if it is **surjective**, it is a **quotient map**.

- [[Open Map]]
- [[Quotient Map]]

### Surjective Smooth Submersion

>[!info]
>By above proposition, a surjective smooth submersion is a [[Quotient Map]].

>[!important] Theorem (Characteristic Property of Surjective Smooth Submersions)
>Suppose $M$ and $N$ are smooth manifolds, and $\pi: M \rightarrow N$ is a **surjective smooth submersion**. 
>
>For any smooth manifold $P$ with or without boundary, a map $F: N \rightarrow P$ is **smooth** *if and only if* $$F \circ \pi$$ is **smooth**.
>
>![[surjective_smooth_submersion.png]]


>[!important] Theorem (Passing Smoothly to the Quotient)
>Suppose $M$ and $N$ are smooth manifolds, and $\pi: M \rightarrow N$ is a **surjective smooth submersion**. 
>
>If $P$ is a smooth manifold with or without boundary and $F: M \rightarrow P$ is a *smooth map* that is **constant** on **the fibers** of $\pi$, $$F(\pi^{-1}\{a\}) = \text{const.},$$
>then there exists a **unique smooth map** $\widetilde{F}: N \rightarrow P$ such that $$\widetilde{F} \circ \pi = F.$$
>
>![[passing_quotient_map.png]]


>[!important] Theorem (Uniqueness of Smooth Quotients)
>Suppose that $M, N_1$, and $N_2$ are smooth manifolds, and $\pi_1: M \rightarrow N_1$ and $\pi_2: M \rightarrow N_2$ are **surjective smooth submersions** that are **constant** on **each other's fibers**. 
>
>Then there exists a **unique diffeomorphism** $F: N_1 \rightarrow N_2$ such that $$F\circ \pi_1 = \pi_2$$
>
>![[unique_smooth_quotient.png]]





-----------
##  Recommended Notes and References

- [[Rank of Smooth Map]]
- [[Differential of a Smooth Map at Point]]
- [[Surjective Function]]

- [[Introduction to Smooth Manifolds by Lee]]