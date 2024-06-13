---
tags:
  - concept
  - math/differential_geometry
keywords:
  - pullback_covector_fields
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Pullback of Covector
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: The Coordinate Representation of Pullback $F^{*}\omega$


>[!important] Definition
>Given the  coordinate representation of covector  $$\omega = \omega_{j}dy^{j},$$ **the pullback of a covector field**  can also be written in the following way:
>$$
> \begin{align}
> F^{*}\omega &= F^{*}(\omega_{j}dy^{j}) \nonumber\\
> &= (\omega_{j} \circ F) F^{*}(dy^{j}) \nonumber\\
> &= (\omega_{j} \circ F)\, d\left(y^{j} \circ F\right)  \\
> &= (\omega_{j} \circ F) \,d\,F^{j}  
> \end{align}
>$$  
>where  $F^j$ is the $j$ th *component function* of $F$ in these coordinates. 


>[!important]
>Using either of these formulas,
>$$
> F^{*}\omega = (\omega_{j} \circ F)\, d\left(y^{j} \circ F\right)
>$$
> and 
>$$ 
> F^{*}\omega = (\omega_{j} \circ F) \,d\,F^{j},  
>$$  
> the computation of pullbacks in coordinates is exceedingly simple.

>[!info]
>In other words, to compute $F^{*}\omega$, all you need to do is **substitute the component functions** of $F$ for the **coordinate functions of $N$** everywhere they appear **in $\omega$**.


- [[Pullback of Covector Fields]]
- [[Coordinate Representation of Covector Field on Manifold]]
- [[Einstein Summation Convention]]


## Exercise

>[!example]
>For $g \in \mathcal{C}^{\infty}(N)$, $q = F(p) \in N$ so that $p= F^{-1}(q) \in M$, 
>$$
> \begin{align*}
> (F_{*}X)_{q}\,g &= dF_{p}(X_{p})g = X_{p}\left(g \circ F\right)
> \end{align*}
>$$ 






-----------
##  Recommended Notes and References

- [[Cotangent Bundle]]

- [[Coordinate Representation of Covector Field on Manifold]]

