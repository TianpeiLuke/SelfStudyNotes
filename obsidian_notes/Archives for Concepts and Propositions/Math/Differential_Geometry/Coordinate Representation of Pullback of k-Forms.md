---
tags:
  - concept
  - math/differential_geometry
keywords:
  - pullback_covector_fields
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Pullback of k-Forms
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Pullback of k-Forms


>[!important] Proposition (Pullback Formula for Top-Degree Forms)
>Let $F: M \rightarrow N$ be a smooth map between $n$-manifolds with or without boundary. 
>
>If $(x^i)$ and $(y^j)$ are *smooth coordinates* on open subsets $U \subseteq M$ and $V \subseteq N$, respectively, and $u$ is a *continuous real-valued function* on $V$, then the following holds on $U \cap F^{-1}(V)$:
>$$
> \begin{align}
> F^{*}\left(u\,dy^{1} \,{\wedge}\ldots{\wedge}\, dy^{n} \right) &= (u \circ F)\;(\det(DF))\;dx^{1} \,{\wedge}\ldots{\wedge}\, dx^{n}  
> \end{align}
>$$ 
> where $DF$ represents **the Jacobian matrix** of $F$ in these coordinates.

^164bfd

- [[Jacobian Matrix and Jacobian Determinant]]

>[!info]
>Note that $$d(y^i \circ F) = dF^{i} = \det(DF)_{j}^{i} \;\; dx^{j}$$

- [[Pullback of k-Form]]
- [[Coordinate Representation of k-Forms]]
- [[Coordinate Representation of Pullback of Tensor Field]]

- [[Einstein Summation Convention]]


## Exercise

>[!important] 
>**Pullback by $F$ operation** can be seen as the **change of variable via map $F$ operation**.

>[!important] Corollary (Change of Coordinates for Differential Forms)
>If $(U, (x^i))$ and $(\widetilde{U}, (\widetilde{x}^j))$ are *overlapping* **smooth coordinate charts** on $M$, then the following identity holds on $U \cap \widetilde{U}$:
>$$
> \begin{align}
> d\widetilde{x}^{1} \wedge \ldots \wedge d\widetilde{x}^{n} &=\det \left(\dfrac{\partial \widetilde{x}^{j}}{\partial x^i}\right)\; dx^1 \wedge \ldots \wedge dx^n. 
> \end{align}
>$$ 




-----------
##  Recommended Notes and References

- [[Pullback of k-Form]]

- [[Coordinate Representation of Pullback of Tensor Field]]
- [[Coordinate Representation of Pullback of Covector]]
- [[Coordinate Representation of k-Forms]]
- [[Coordinate Representation of Differential at Point]]

- [[Differential k-Form on Manifold]]

