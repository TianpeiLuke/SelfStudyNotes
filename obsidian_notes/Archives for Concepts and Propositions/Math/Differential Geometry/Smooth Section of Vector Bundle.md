---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_section_vector_bundle
topics:
  - differential_geometry
name: Smooth Section of Vector Bundle
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Smooth Section of Vector Bundle

>[!important] Definition
>If $M$ is a smooth manifold with or without boundary and $E$ is a *smooth vector bundle*, a **smooth (local or global) section** of $E$ is one that is a *smooth map* from its domain to $E$.


- [[Section of Vector Bundle]]
- [[Smooth Bundle and Trivial Bundle]]
- [[Smooth Vector Field on Manifold]]




## Explanation

>[!important] Definition
>Suppose  $(\sigma_i)$ is a *smooth local frame* for $E$ over some open subset $U \subseteq M$. 
>
>If $\tau: M \rightarrow E$ is a *rough section*, the value of $\tau$ at an arbitrary point $p \in U$ can be written $$\tau(p) = \tau^{i}(p)\sigma_i(p)$$ for some *uniquely determined numbers* $$(\tau^1(p), \ldots, \tau^{k}(p)).$$ 
>
>This defines $k$ functions $\tau^i: U \rightarrow \mathbb{R}$, called the **component functions** of $\tau$ with respect to the *given local frame*.

- [[Einstein Summation Convention]]
- [[Local and Global Frames for Vector Bundle]]

>[!important] Proposition
>Let $\pi: E \rightarrow M$ be a *smooth vector bundle*, and let $\tau: M \rightarrow E$ be a *rough section*. 
>
>If  $(\sigma_i)$ is a **smooth local frame** for $E$ over *an open subset* $U \subseteq M$, then $\tau$ is **smooth** on $U$ *if and only if* its **component functions** with respect to $(\sigma_i)$ are **smooth**.



















-----------
##  Recommended Notes and References

- [[Vector Bundle]]
	- [[Tangent Bundle]]
	- [[Cotangent Bundle]]

- [[Smooth Vector Field on Manifold]]
- [[Smooth Covector Field on Manifold]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]