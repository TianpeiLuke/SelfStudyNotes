---
tags:
  - concept
  - math/differential_geometry
keywords:
  - differential_real_function_coordinate
topics:
  - differential_geometry
name: Coordinate Representation of Differential
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Differential

>[!important] Definition
>Let $(x^i)$ be smooth coordinates on an open subset $U \subseteq M$, and let $(\lambda^i)$ be the corresponding *coordinate coframe* on $U$. 
>
>Write $df$ in coordinates as $$df_p = A_i(p) \lambda^i |_p$$ for *some functions* $A_i: U \rightarrow \mathbb{R}$,  then the definition of $df$ implies
>$$
> \begin{align*}
> A_i(p) &= df_{p}\left(\frac{\partial }{ \partial x^{i}}\Bigr|_{p}\right) =\frac{\partial }{ \partial x^{i}}\Bigr|_{p} f = \frac{\partial f}{ \partial x^{i}}\Bigr|_{p}.
> \end{align*}
>$$ 
>
>This yields the following formula for **the coordinate representation** of $df$:
>$$
> \begin{align}
> df_p = \frac{\partial f}{ \partial x^{i}}(p) \; \lambda^i |_p 
> \end{align}
>$$  

- [[Differential as Covector Field]]
- [[Coordinate Representation of Covector Field on Manifold]]

>[!info]
>Thus, the **component functions** of $df$ in any smooth coordinate chart are **the partial derivatives of $f$** with respect to those coordinates. 
>
>Because of this, we can think of $df$ as *an analogue of the classical gradient*, reinterpreted in a way that makes **coordinate-independent sense** on a manifold.


- [[Differential as Covector Field]]
- [[Smooth Covector Field on Manifold]]
- [[Einstein Summation Convention]]


## Explanation

- [[Coordinate Representation of Covector Field on Manifold]]

>[!info]
>If we apply above formula to the special case in which $f$ is one of the **coordinate functions** $x^j: U \rightarrow \mathbb{R}$, we obtain
>$$
> \begin{align*}
> d x^{j} |_p  &= \frac{\partial {x^{j}}}{\partial x^{i}}(p) \; \lambda^i |_p = \delta_{i}^{j}\; \lambda^i |_p =  \lambda^j |_p.
> \end{align*}
>$$ 

>[!important]
In other words, **the coordinate covector field** $\lambda^j$ is none other than **the differential $dx^j$**.


>[!info] 
Therefore, the coordinate formula for $df_p$ can be rewritten as
>$$
> \begin{align}
> df_p =\frac{\partial f}{ \partial x^{i}}(p)\; d x^{i} |_p.  
> \end{align}
>$$  
>or as **an equation between covector fields** instead of *covectors*. 

>[!important] Definition
>The **coordinate representation of differential $df$** is
>$$
> \begin{align}
> df = \frac{\partial f}{ \partial x^{i}}\; d x^{i}.    
> \end{align}
>$$  
>Thus, we have recovered the familiar classical expression for the differential of a
> function $f$ in coordinates. 

>[!info]
> Henceforth, we *abandon the notation* $\lambda^i$ for **the coordinate coframe**, and use $dx^i$ instead. 




-----------
##  Recommended Notes and References

- [[Smooth Section of Vector Bundle]]
- [[Local and Global Frames for Vector Bundle]]


- [[Basis of Vector Space]]