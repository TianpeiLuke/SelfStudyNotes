---
tags:
  - entry_point
  - concept
  - math/topology
  - math/differential_geometry
keywords: 
topics:
  - topology
  - differential_geometry
name: 
date of note: 2024-05-06
---
## Background

>[!info]
>**Tangent Vector Fields** and its **Dual** (**Covector Fields**) play a *critical role* in analyzing both
>- the **analytical properties** of *smooth functions* and 
>- the **geometrical properties** of *smooth manifold* 
>
>in differential geometry.

>[!info]
>- They **generalize** several key *geometric concepts* from local neighborhood to entire surface. 
>	- Examples such as *tangent vector*  and the *measures of tangent vector* at a point
>	- These concepts provide a **holistic view** of geometric properties of the nonlinear smooth manifold with **linearization**.
>
>- Vector field and covector field also represent a **global abstraction** of the **derivative and differential operations** on smooth maps. 
>	- Both *derivative and differential operations* play key roles to understand the **local variation property** of smooth map and their **dynamical evolution** over time.



##  List of Concepts

### Vector Bundle and its Section

- [[Vector Bundle]]
- [[Smooth Bundle and Trivial Bundle]]
- [[Coordinate Representation of Element in Vector Bundle]]
- [[Section of Vector Bundle]]
- [[Smooth Section of Vector Bundle]]
- [[Space of all Smooth Sections of Vector Bundle]]
- [[Local and Global Frames for Vector Bundle]]

### From Tangent Vector to Vector Field

- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Tangent Vector as Velocity of Smooth Curves]]
- [[Tangent Space Definition and Development]]
- [[Tangent Space as Finite Dimensional Vector Space]]
- [[Tangent Bundle]]
- [[Coordinate Representation of Element in Tangent Bundle]]
- [[Vector Field on Manifold]]
- [[Vector Field along Subset of Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Local and Global Frame for Tangent Bundle]]
- [[Coordinate Representation of Vector Field on Manifold]]

### Transform between Vector Fields

- [[Smooth Maps on Space of Vector Fields]]: **F-related**
- [[Pushforward of Vector Fields]]

### Global Flows, Local Flows and Integral Curves

- [[Integral Curve of Vector Field]]
- [[Global Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Maximal Integral Curve of Vector Field]]
- [[Fundamental Theorem on Flows]]
- [[Lie Derivative of Vector Field]]


### From Differential and Covector to Covector Field

- [[Differential of a Smooth Map at Point]]
- [[Covector on Vector Space]]
- [[Covector Space]]
- [[Cotangent Space]]
- [[Cotangent Bundle]]
- [[Coordinate Representation of Element in Cotangent Bundle]]
- [[Covector Field on Manifold]]
- [[Smooth Covector Field on Manifold]]
- [[Space of all Smooth Covector Fields on a Manifold]]
- [[Local and Global Coframes for Cotangent Bundle]]
- [[Coordinate Representation of Covector Field on Manifold]]
- [[Differential as Covector Field]]
- [[Coordinate Representation of Differential]]

### Transform between Covector Fields

- [[Pullback of Covector Fields]]
- [[Coordinate Representation of Pullback of Covector]]



## Duality between Tangent and Cotangent 

| base                                               | smooth manifold $M$                                                                                                                          | smooth manifold $M$                                                                                                                             |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| element                                            | $\varphi(p) = (x^1, \ldots, x^{n})$                                                                                                          | $\varphi(p) = (x^1, \ldots, x^{n})$                                                                                                             |
| **vector space** (**fiber**) at $p$                | **tangent space**  $$T_{p}M$$                                                                                                                | **cotangent space**, **dual** of tangent space $$T_{p}^{*}M = (T_{p}M)^{*}$$                                                                    |
| dimension of vector space                          | $n$                                                                                                                                          | $n$                                                                                                                                             |
| **basis** of vector space                          | $$\left(\dfrac{\partial}{\partial x^i}(p)\right)_{i=1}^n$$                                                                                   | $$(dx^i(p))_{i=1}^n$$                                                                                                                           |
| *element* in vector space                          | **tangent vector**: $\mathcal{C}^{\infty}(M) \rightarrow \mathbb{R}$ $$v = v^{i}\dfrac{\partial}{\partial x^i}(p)$$                          | **cotangent vector**: $T_pM \rightarrow \mathbb{R}$ $$\omega = \xi_{i}\;dx^i(p)$$                                                               |
| **vector bundle**                                  | **tangent bundle**<br> $$TM =  \bigsqcup_{p\in M}T_{p}M$$                                                                                    | **cotangent bundle** <br>$$T^{*}M =  \bigsqcup_{p\in M}T_{p}^{*}M$$                                                                             |
| **coordinate** of element in bundle                | $(x^1(p), \ldots, x^{n}(p),  v^1, \ldots, v^{n})$                                                                                            | $(x^1(p), \ldots, x^{n}(p),  \xi_1, \ldots, \xi_{n})$                                                                                           |
| **section**                                        | **vector field** <br>$$X = X^{i}\dfrac{\partial }{ \partial x^{i}}$$ <br>where $X_{p} \in T_{p}M$ for each $p\in M$                          | **covector field** <br>$$\omega = \xi_{i} dx^{i}$$<br><br> where $\omega_p \in T_{p}^{*}M$ for each $p\in M$                                    |
| **vector space of sections**                       | $\mathfrak{X}(M) \equiv \Gamma(TM)$                                                                                                          | $\mathfrak{X}^{*}(M) \equiv \Gamma(T^{*}M)$                                                                                                     |
| **frame**                                          | **coordinate vector fields**<br> $$\left(\dfrac{\partial}{\partial x^i}\right)_{i=1}^n$$                                                     | **coordinate covector fields** <br>$$(dx^i)_{i=1}^n$$                                                                                           |
| **duality**                                        | $$\xi  \left(\dfrac{\partial }{ \partial x^{i}}(p)\right) (dx^{j}(p)) = \delta_{i}^{j}$$                                                     | $$dx^{j}(p)\left(\dfrac{\partial }{\partial x^{i}}(p)\right)  = \delta_{i}^{j}$$                                                                |
| **change of coordinates**                          | **contravariant** <br>$$\widetilde{v}^{j}= \dfrac{\partial \widetilde{x}^{j}}{ \partial x^{i}}(p)\, v^{i}$$                                  | **covariant**<br> $$\omega_{i} = \frac{\partial \widetilde{x}^{j}}{\partial x^{i}}(p)\,\widetilde{\omega}_{j}$$                                 |
| **Operator between Sections** induced by functions | **Pushforward**  $F_{*}: \mathfrak{X}(M) \rightarrow \mathfrak{X}(N)$ $$(F_{*}X)_{q} = dF_{F^{-1}(q)}(X_{F^{-1}(q)}),\; q\in N$$<br><br><br> | **Pullback**: $F^{*}: \mathfrak{X}^{*}(N) \rightarrow \mathfrak{X}^{*}(M)$ $$(F^{*}\omega)_p = dF_{p}^{*}\left(\omega_{F(p)}\right),\; p\in M$$ |
| definition of  functions that induced the operator | $F: M \rightarrow N$ **diffeomorphism**  $dF_{p}: T_pM \rightarrow T_{F(p)}N$                                                                | no additional requirement for $F$<br>$dF_{p}^{*}:  T_{F(p)}^{*}N \rightarrow T_{p}^{*}M$ <br>is **dual (adjoint) operator** of $dF_p$           |








-----------
##  Recommended Notes and References

- [[Tangent Space and Tangent Bundle]]
- [[Cotangent Space and Differential of Map]]

- [[Introduction to Smooth Manifolds by Lee]]

