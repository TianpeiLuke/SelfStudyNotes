---
tags:
  - concept
  - math/differential_geometry
keywords:
  - covector_field
topics:
  - differential_geometry
name: Covector Field on Manifold
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Covector Field on Manifold

>[!important] Definition
>If $M$ is a *smooth manifold* with or without boundary, a **covector field** on $M$ is a **section** *of the map* $$\pi: T^{*}M \rightarrow M.$$ 
>
>More concretely, a **covector field** is a *continuous map* $X: M \rightarrow T^{*}M$, usually written $p \mapsto \omega_p$, with the property that
>$$
> \begin{align}
> \pi \circ \omega = \text{Id}_{M},
> \end{align}
>$$  
>or **equivalently**, $\omega_p \in T_{p}^{*}M$ for each $p \in M$.

- [[Section of Continuous Function]]
- [[Cotangent Bundle]]

>[!important] Definition
>A *local (or global) section* of $T^{*}M$ is called a **covector field** or a **differential 1-form**.

- [[Section of Vector Bundle]]
- [[Cotangent Bundle]]

## Explanation

>[!info]
>A **covector field** is seen as a **global generalization** of a *cotangent vector*. 

- [[Covector on Vector Space]]

## Smooth and Rough Covector Fields

>[!info]
>Like sections of other bundles, covector fields without further qualification are assumed to be merely *continuous*; when we make different assumptions, we use the terms **rough covector field** and **smooth covector field** with the obvious meanings.

- [[Smooth Vector Field on Manifold]]




-----------
##  Recommended Notes and References

- [[Section of Vector Bundle]]

- [[Section of Continuous Function]]


- [[Introduction to Smooth Manifolds by Lee]]