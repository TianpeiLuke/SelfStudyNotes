---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_covector_field
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Covector Field on Manifold
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Covector Field on Manifold

>[!important] Definition
>In any smooth local coordinates on an open subset $U \subseteq M$; **a (rough) covector field** $\omega$ can be written in terms of **the coordinate covector fields** $(\lambda^i)$ as  $$\omega_{i}\,\lambda^i$$ for $n$ **functions** $\omega_i: U \rightarrow \mathbb{R}$ called the **component functions** of $\omega$. 
>
>They are characterized by
>$$
> \begin{align*}
> \omega_{i} &= \omega_{p}\left(\frac{\partial }{\partial x^{i}} \Bigr|_{p}\right).
> \end{align*}
>$$ 

- [[Smooth Covector Field on Manifold]]
- [[Einstein Summation Convention]]

>[!important] Definition
>The **the coordinate covector fields $\omega$** is
>$$
> \begin{align}
> \omega = \omega_{i}\,\; d x^{i}.    
> \end{align}
>$$  
>where
>$$dx^{i}\left(\frac{\partial }{\partial x^{j}} \Bigr|_{p}\right) = \delta_{j}^{i}, \quad \forall i,j =1,\ldots, n, p \in M$$ 

- [[Coordinate Representation of Differential]]

>[!important]
>In differential geometry, in order to apply [[Einstein Summation Convention]], the **component index of covector field is on the bottom**, since the basis coframe has index on the *top*.


## Specification via Differential

>[!info]
>Recall  **the coordinate representation** of $df$:
>$$
> \begin{align}
> df_p = \frac{\partial f}{ \partial x^{i}}(p) \; \lambda^i |_p 
> \end{align}
>$$  


>[!info]
>If we apply above formula to the special case in which $f$ is one of the **coordinate functions** $x^j: U \rightarrow \mathbb{R}$, we obtain
>$$
> \begin{align*}
> d x^{j} |_p  &= \frac{\partial {x^{j}}}{\partial x^{i}}(p) \; \lambda^i |_p = \delta_{i}^{j}\; \lambda^i |_p =  \lambda^j |_p.
> \end{align*}
>$$ 

>[!important]
In other words, **the coordinate covector field** $\lambda^j$ is none other than **the differential $dx^j$**.
















-----------
##  Recommended Notes and References

- [[Smooth Section of Vector Bundle]]
- [[Local and Global Frames for Vector Bundle]]

- [[Basis of Vector Space]]
- [[Vector Space over a Field]]


