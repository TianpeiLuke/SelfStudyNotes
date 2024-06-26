---
tags:
  - concept
  - math/differential_geometry
keywords:
  - section_vector_bundle
topics:
  - differential_geometry
name: Section of Vector Bundle
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Section of Vector Bundle

>[!important] Definition
>Let $\pi: E \rightarrow M$ be a *vector bundle*. 
>
>A **section** of $E$ (sometimes called a **cross section**) is a *section (right inverse)* of the *map* $\pi$, that is, a *continuous map*  $\sigma: M \rightarrow E$ satisfying
>$$
> \begin{align*}
> \pi \circ \sigma =  \text{Id}_M. 
> \end{align*} 
>$$ 
>This means that $\sigma(p)$ is an element of the *fiber* $E_p$ for each $p \in M$.

- [[Section of Continuous Function]]
- [[Vector Bundle]]
- [[Vector Field on Manifold]]
- [[Covector Field on Manifold]]

>[!important] Definition
>More generally, a **local section** of $E$ is a *continuous* map $\sigma: U \rightarrow E$ defined on some *open subset* $U \subseteq M$ and satisfying $$\pi \circ \sigma =  \text{Id}_U.$$ 

>[!important] Definition
>To emphasize the distinction, a section defined on **all of** $M$ is sometimes called a **global section**. 

>[!info]
>Note that a *local section* of $E$ over $U \subseteq  M$ is the *same* as a *global section* of *the restricted bundle* $E|_{U}$.

>[!important] Definition
>The **zero section** of $E$ is the *global section* $\xi: M \rightarrow E$ defined by
>$$
> \begin{align*}
> \xi(p) &= 0 \in E_{p}, \quad \forall p \in M.
> \end{align*}
>$$


>[!important] Definition
>As in the case of vector fields, the **support** of a *section* $\sigma$ is the **closure** of the set $$\set{p \in M:\;  \sigma(p) \neq 0}.$$


## Explanation








-----------
##  Recommended Notes and References

- [[Section of Vector Bundle]]

- [[Tangent Bundle]]
- [[Cotangent Bundle]]


- [[Section of Continuous Function]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]