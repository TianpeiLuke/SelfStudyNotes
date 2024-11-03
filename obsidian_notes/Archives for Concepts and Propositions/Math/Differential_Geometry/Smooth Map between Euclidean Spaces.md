---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_map
topics:
  - differential_geometry
name: Smooth Map between Euclidean Spaces
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Smooth Map between Euclidean Spaces

>[!important] Definition
>If $U$ and $V$ are *open* subsets of Euclidean spaces $\mathbb{R}^n$ and $\mathbb{R}^m$, respectively, a function $F: U \rightarrow V$ is said to be **smooth** (or $\mathcal{C}^{\infty}$ , or **infinitely differentiable**) if each of its component functions has *continuous partial derivatives* of *all orders*. 

- [[Space of Continuous Differentiable Functions]]

## Explanation

## Properties

>[!info]
>The following shows that **smoothness** is a **local** property 

>[!important] Proposition 
>Let $M$ and $N$ be smooth manifolds with or without boundary, and let $F: M \rightarrow N$ be a map.
>- If every point $p \in M$ has a *neighborhood* $U$ such that the **restriction** $F|_{U}$ is **smooth**, then $F$ is **smooth**.
>- Conversely, if $F$ is **smooth**, then its **restriction** to *every open subset* is **smooth.**

>[!important] Corollary (Gluing Lemma for Smooth Map)
> Let $M$ and $N$ be smooth manifolds with or without boundary, and let $\set{U_{\alpha}}_{\alpha \in A}$ be an *open cover* of $M$. 
> 
> Suppose that for each $\alpha \in A$, we are given a smooth map $F_{\alpha}: U_{\alpha} \rightarrow N$ such that the maps **agree on overlaps**: 
> $$F_{\alpha}|_{U_{\alpha}\cap U_{\beta}} = F_{\beta}|_{U_{\alpha}\cap U_{\beta}}$$ 
> for all $\alpha$ and $\beta$. 
> 
> Then there exists a **unique smooth map** $F: M \rightarrow N$ such that $F|_{U_{\alpha}} = F_{\alpha}$, for each $\alpha \in A$.

- [[Coordinate Representation of Smooth Map]]
## Examples

>[!example]
>Let $M, N$ and $P$ be smooth manifolds with or without boundary.
> - Every **constant map** $c: M \rightarrow N$ is *smooth*.
> - The **identity map** of $M$ is smooth.
> - If $U \subseteq M$ is an **open submanifold** with or without boundary, then the **inclusion
> map** $U \xhookrightarrow{} M$ is smooth.
> - If $F: M \rightarrow N$ and $G: N \rightarrow P$  are *smooth*, then so is the **composite map** $G \circ F: M \rightarrow P.$

>[!example]
>Any map from a **zero-dimensional manifold** into a **smooth manifold** with or without boundary is automatically smooth, because each *coordinate representation* is **constant**.

>[!example]
>If the **circle** $\mathbb{S}^1$ is given its *standard smooth structure*, the map $\epsilon: \mathbb{R}\rightarrow \mathbb{S}^1$ defined by 
>$$\epsilon(t) = \exp \left(2\pi i t\right)$$ 
>is **smooth**, because with respect to any angle coordinate $\theta$ for $\mathbb{S}^1$ it has a coordinate representation of the form $$\widehat{\epsilon}(t) = 2 \pi t + c$$ 
>for some constant $c$, as you can check.

>[!example]
>The map $\epsilon^n: \mathbb{R}^{n} \rightarrow \mathbb{T}^n$ defined by 
>$$\epsilon^n(t) = \left(\exp\left(2\pi i x^1\right), \ldots, \exp \left(2\pi i x^n\right)\right)$$ 
>is **smooth** since **$n$-torus** $\mathbb{T}^n = \mathbb{S}\times \ldots \times \mathbb{S}$.






-----------
##  Recommended Notes and References

- [[Continuous Function]]