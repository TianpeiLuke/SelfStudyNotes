---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_vector_field
topics:
  - differential_geometry
name: Smooth Vector Field
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Smooth Vector Field on Manifold

>[!important] Definition
>When the map $X: M \rightarrow TM$ is **smooth** and the *tangent bundle* $TM$ is given a **smooth manifold structure**,  $X$ is a **smooth vector field**. 

- [[Vector Field on Manifold]]
- [[Tangent Bundle]]

>[!info]
> In addition, for some purposes it is useful to consider maps from $M$ to $TM$ that would be vector fields except that they *might not be continuous*. 


>[!important] Definition
> A **rough vector field** on $M$ is a *not necessarily continuous* map $X: M \rightarrow TM$ satisfying 
> $$
> \begin{align}
> \pi \circ X = \text{Id}_{M}
> \end{align}
> $$
> where $\pi: TM \to M$ is the section of the tangent bundle.


## Explanation



## Coordinate Representation

- [[Coordinate Representation of Vector Field on Manifold]]

## As Derivation on Smooth Functions

- [[Vector Fields as Total Derivation of Smooth Maps]]

## Examples

>[!example]
>If $(U, (x^i))$ is any *smooth chart* on $M$, the assignment
>$$
> \begin{align*}
> p \mapsto \frac{\partial }{ \partial x^{i}}\Bigr|_{p}
> \end{align*} 
>$$ 
> determines a *vector field* on $U$, called **the $i$-th coordinate vector field** and denoted by $$\frac{\partial }{ \partial x^{i}}$$ 
> (without $p$ since it is now a function of $p$). 
> 
> It is **smooth** because its component functions are *constants*.

>[!example]
>The *vector field* $V$ on $\mathbb{R}^n$ whose value at $x \in \mathbb{R}^n$ is
>$$
> \begin{align*}
> V_x & = x^{1}\,\frac{\partial }{ \partial x^{1}}\Bigr|_{x} + \ldots + x^{n}\,\frac{\partial }{ \partial x^{n}}\Bigr|_{x}.
> \end{align*}
>$$  
>It is **smooth** because its coordinate functions are **linear**. It **vanishes at the origin**, and **points radially outward** *everywhere else*. 
>
>It is called **the Euler vector field** because of its appearance in **Euler’s homogeneous function theorem**.






-----------
##  Recommended Notes and References

- [[Smooth Section of Vector Bundle]]

- [[Vector Field on Manifold]]
- [[Tangent Bundle]]


- [[Introduction to Smooth Manifolds by Lee]]