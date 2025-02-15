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
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
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
- [[Change of Coordinates between Vector Fields]]

### Global Flows, Local Flows and Integral Curves

- [[Integral Curve of Vector Field]]
- [[Global Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Maximal Integral Curve of Vector Field]]
- [[Fundamental Theorem on Flows]]
- [[Lie Derivative of Vector Field]]
- [[Matrix Exponential as Global Flow in General Linear Group]]

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
- [[Change of Coordinates for Covector Fields and Differentials]]

### Tensor on Riemannian Manifold

- [[Riemannian Metric and Riemannian Manifold]]
- [[Flat Operator and Lower Index of Vector Field]]
- [[Sharp Operator and Raise Index of Covector Field]]
- [[Tangent-Cotangent Isomorphism in Riemannian Manifold]]

- [[Gradient of Smooth Map]]
- [[Coordinate Representation of Gradient]]
- [[Riemannian Volume Form]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Coordinate Representation of Divergence Operator]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Coordinate Representation of Laplace Operator]]

## Derivatives of Vector Fields and Tensor Fields

- [[Summary of Differentiation of Vector Field]]

### Lie Derivative

>[!info]
>**Lie derivative** measure the **directional derivative** of **tangent vector fields** *along the* **flow** of another *tangent vector fields*.
>
>The key is to use a **flow** on smooth manifold to define the **direction** in the **directional derivative**


- [[Lie Bracket of Vector Fields]]
- [[Coordinate Formula for Lie Bracket of Vector Fields]]

- [[Integral Curve of Vector Field]]
- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Fundamental Theorem on Flows]]

- [[Lie Derivative of Vector Field]]
- [[Lie Algebra as Vector Space with Lie Bracket]]
- [[Lie Group]]

### Covariant Derivative of Tensor Field


>[!info]
>**Covariant derivative** measure the **directional derivative** of **sections of vector bundle** *along the* **tangent direction** defined by *tangent vector fields*.
>
>The idea is to **project** the directional derivative from *ambient vector space* to **the tangent space of the submanifold.**

#### Connection, Covariant Derivative of Tensor Field and Affine Connection

- [[Development of Connection from Euclidean to Manifold]]
- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Affine Connection on Tangent Bundle]]
- [[Affine Connection of Basis Frames and Connection Coefficient]]
- [[Coordinate Representation of Connection]]
- [[Difference Tensor based on Affine Connection]]
- [[Space of all Affine Connections]]

#### Covariant Derivatives

- [[Total Covariant Derivative]]
- [[Second Covariant Derivatives]]
- [[Covariant Hessian Tensor]]

#### Parallel Transport and Geodesic Curve

- [[Vector Field Along a Curve]]
- [[Covariant Derivative Along a Curve]]
- [[Coordinate Representation of Covariant Derivative Along a Curve]]

- [[Geodesic on Manifolds]]
- [[Coordinate Representation of Geodesic and Geodesic Equations]]
- [[Maximal Geodesic and Geodesic Segment]]

- [[Parallel Transport of Tensor Field along Curve]]
- [[Coordinate Representation of Vector Field Parallel Along a Curve]]

- [[Parallel Transport Algebraic Definitions]]
- [[Covariant Derivative from Parallel Transport]]

#### Riemannian Connection

- [[Metric Connection for Riemannian Manifold]]
- [[Symmetric Connection]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Christoffel Symbols]]



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

- [[Concepts related to Tangent Space and Tangent Bundle]]
- [[Cotangent Space and Differential of Map]]

- [[Introduction to Smooth Manifolds by Lee]]

