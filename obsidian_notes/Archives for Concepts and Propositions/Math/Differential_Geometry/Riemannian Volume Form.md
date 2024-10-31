---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
keywords:
  - riemannian_volume_form
  - integral_on_riemannian_manifold
topics:
  - differential_geometry
  - riemannian_geometry
name: Riemannian Volume Form
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Riemannian Volume Form

>[!important] Proposition
>Let $(\mathcal{M}. g)$ be an **oriented Riemannian $n$- manifold** with or without boundary.
>
>There is a **unique** $n$-form $dV_{g}$ on $\mathcal{M}$, called the **Riemannian volume form**, characterized by *any* of the following properties
>- If $(\epsilon^1\,{,}\ldots{,}\,\epsilon^{n})$ is any *local oriented orthonormal coframe* for $T^{*}\mathcal{M}$, then $$dV_{g} := \epsilon^1 \,{\wedge}\ldots{\wedge}\, \epsilon^n.$$
>- If $(E_{1}\,{,}\ldots{,}\,E_{n})$ is any *local oriented orthonormal frame* for $T\mathcal{M}$, then $$dV_{g}(E_{1}\,{,}\ldots{,}\,E_{n}) := 1.$$
>- If $(x^1\,{,}\ldots{,}\,x^{n})$ is any *oriented local coordiantes* for $T^{*}\mathcal{M}$, then $$dV_{g} := \sqrt{ \det(g_{i,j}) }\;dx^1 \,{\wedge}\ldots{\wedge}\,dx^n.$$

^e3acc5

- [[Riemannian Metric and Riemannian Manifold]]
- [[Local and Global Frame for Tangent Bundle]]
- [[Local and Global Coframes for Cotangent Bundle]]
- [[Wedge Product]]
- [[Orientation of Manifolds]]
- [[Orientated Smooth Coordinate Chart]]


### Integral on Riemannian Manifold

![[Integration on Riemannian Manifold and Volume of Compact Riemannian Manifold#^99e529]]


- [[Integration on Riemannian Manifold and Volume of Compact Riemannian Manifold]]

### Regular Domain

>[!important] Definition
>A subset of Riemannian manifold $D \subseteq \mathcal{M}$ is called a **regular domain**, i.e. a *closed, embeded codimension-0 submanifold* if we can apply the definition of *integration* on $D$ with its *induced metric* $g_{D}$, i.e. we can define $$\int_{D} f\,dV_{g_{D}}$$

- [[Embedded Submanifold]]
- [[Regular Point and Regular Value of Smooth Map]]



## Explanation



## Divergence Operator


- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Divergence Theorem on Riemannian Manifold]]





-----------
##  Recommended Notes and References


- [[Orientations of Manifold determined by k-Form]]
- [[Orientations of Manifold determined by Coordinate Atlas]]
- [[Differential k-Form as Infinitesimal Volume]]
- [[Differential k-Form on Manifold]]


- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]] pp 30