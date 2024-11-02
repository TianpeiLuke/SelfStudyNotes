---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords:
  - rank_theorem
topics:
  - differential_geometry
  - linear_algebra
name: Rank Theorem
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: The Rank Theorem


>[!important] Rank Theorem
>Suppose $M$ and $N$ are smooth manifolds of dimensions $m$ and $n$, respectively, and  $F: M \rightarrow N$ is a **smooth map with constant rank $r$**. 
>
>For each $p \in M$ there exist *smooth charts* $(U, \varphi)$ for $M$ centered at $p$ and $(V,\psi)$ for $N$ centered at $F(p)$ such that $F(U) \subseteq V$, in which $F$ has a **coordinate representation** of the form
>$$
> \begin{align}
> \widehat{F}(x^1,\ldots, x^r, x^{r+1},\ldots, x^m) &= (x^1,\ldots, x^r, 0,\ldots, 0).  
> \end{align}
>$$ 
>
> In particular, 
>- if $F$ is a **smooth submersion**, this becomes
>$$ 
> \begin{align}
> \widehat{F}(x^1,\ldots, x^n, x^{n+1},\ldots, x^m) &=  (x^1,\ldots, x^n).  
> \end{align}
>$$ 
>- if $F$ is a **smooth immersion**, it is
>$$
> \begin{align}
> \widehat{F}(x^1,\ldots, x^m) &=  (x^1,\ldots, x^m, 0,\ldots, 0). 
> \end{align}
>$$ 

- [[Jacobian Matrix and Jacobian Determinant]]
- [[Rank of Smooth Map]]
- [[Smooth Submersion]]
- [[Smooth Immersion]]

- [[Canonical Inclusion]]
- [[Canonical Projection]]


>[!info]
>The Rank Theorem is a **local statement**. However, it has the following powerful **global consequence**.

>[!important] Global Rank Theorem
>Let $M$ and $N$ be smooth manifolds, and suppose $F: M \rightarrow N$ is a **smooth map of constant rank**.
>
>- If $F$ is **surjective**, then it is a **smooth submersion**.
>- If $F$ is **injective**, then it is a **smooth immersion**.
>- If $F$ is **bijective**, then it is a **diffeomorphism**.
>

- [[Inverse Function Theorem]]
- [[Smooth Submersion]]
- [[Smooth Immersion]]
- [[Diffeomorphism]]

### Manifold with Boundary

>[!info]
>In the context of manifolds with boundary, we need the rank theorem only in one special case: that of a **smooth immersion** whose *domain* is a **smooth manifold with boundary**.


>[!important] Local Immersion Theorem for Manifold with Boundary
>Suppose $M$ is a smooth $m$-manifold with boundary, $N$ is a smooth $n$-manifold, and $F: M \rightarrow N$ is a **smooth immersion.** 
>
>For any $p \in \partial M$; there exist a **smooth boundary chart** $(U,\varphi)$ for $M$ centered at $p$ and a *smooth coordinate chart* $(V, \psi)$ for $N$ centered at $F(p)$ with $F(U) \subseteq V$, in which $F$ has the **coordinate representation**
>$$
> \begin{align}
> \widehat{F}(x^1,\ldots, x^m) &=  (x^1,\ldots, x^m, 0,\ldots, 0)
> \end{align}
>$$ 

- [[Canonical Inclusion]]
- [[Canonical Projection]]

## Explanation

>[!info]
>According to the rank theorem, *every* **smooth map with full rank** can be simplified as a composite of the **projection map** with **inclusion map** i.e. **additional zero padding**.
>
>$$
>F \text{ smooth with full rank } \implies dF_{p} \text{ full rank all }p  \implies F \simeq \iota \circ \pi
>$$



>[!important] Definition
>The **canonical representation** for a **smooth submersion** 
>$$
>\widehat{F}(x^1,\ldots, x^r, x^{r+1},\ldots, x^m) = (x^1,\ldots, x^r, 0,\ldots, 0).
>$$
 >is called the **canonical surjection** or the **projection map**, denoted as $\pi$;  
 
 >[!important] Definition
 >Similarly, the **canonical representation** for a **smooth immersion** in
 >$$
 >\widehat{F}(x^1,\ldots, x^m) =  (x^1,\ldots, x^m, 0,\ldots, 0).
 >$$
 >is called the **canonical injection** or **the inclusion map**, denoted as $\iota$.

>[!info]
>The Rank Theorem states that 
>- every **smooth immersion** is an **inclusion map locally** and
>- every **smooth submersion** is a **projection map locally**, 
>
>both regardless of the form of the map itself.


>[!info]
>From Global Rank Theorem, for $F$ has constant rank, i.e. $\text{rank}(dF_{p}) = const.$, then
>$$
>F \text{ surjective/injective/bijective} \implies dF_{p} \text{ surjective/injective/bijective};
>$$
>

| If $F$ is of **constant rank** and it is ... | then $dF_{p}$ for all $p$ is ...            |
| -------------------------------------------- | ------------------------------------------- |
| [[Surjective Function]]                      | [[Surjective Function]]                     |
| [[Injective Function]]                       | [[Injective Function]]                      |
| [[Bijective Function and Inverse Function]]  | [[Bijective Function and Inverse Function]] |








-----------
##  Recommended Notes and References


- [[Range and Kernel of Linear Map]]
- [[Rank and Nullity of Linear Map]]
- [[Rank–Nullity Theorem]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Principles of Mathematical Analysis by Rudin]] pp 228 - 229