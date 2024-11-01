---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
keywords:
  - metric_connection
  - riemannian_manifold
topics:
  - differential_geometry
  - riemannian_geometry
name: Metric Connection
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Metric Connection

>[!important] Definition
>Let $g$ be a *Riemannian* or *pseudo-Riemannian metric* on a *smooth manifold* $M$ (with or without boundary). 
>
>A connection $\nabla$ on $TM$ is said to be **compatible with** $g$, or to be a **metric connection**, if it satisfies the following *product rule* for all $X, Y, Z \in \mathfrak{X}(M)$:
>$$
> \begin{align}
>  \nabla_{Z}(\left\langle X\,,\,Y \right\rangle_{g}) &= \left\langle \nabla_{Z}X\,,\, Y \right\rangle_{g} + \left\langle  X\,,\,  \nabla_{Z}Y \right\rangle_{g} \\[5pt]
> \Leftrightarrow Z\left\langle  X\,,\, Y   \right\rangle_{g} &= \left\langle \nabla_{Z}X\,,\, Y \right\rangle_{g} + \left\langle  X\,,\,  \nabla_{Z}Y \right\rangle_{g} 
> \end{align}
>$$  

- [[Riemannian Metric and Riemannian Manifold]]
- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Tangent Bundle]]
- [[Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]


## Explanation


## Characterization of Metric Connection

>[!important] Proposition
>Let $(\mathcal{M}, g)$ be a *Riemannian* or *pseudo-Riemannian manifold* (with or without boundary), and let $\nabla$ be a *connection* on $T\mathcal{M}$. The following conditions are **equivalent**:
>- $\nabla$ is **compatible** with $g$: $$\nabla_{Z}(\left\langle X\,,\,Y \right\rangle_{g}) = \left\langle \nabla_{Z}X\,,\, Y \right\rangle_{g} + \left\langle  X\,,\,  \nabla_{Z}Y \right\rangle_{g}.$$
>-  $g$ is **parallel** *with respect to* $\nabla$: $$\nabla g \equiv 0.$$
>-  In terms of any smooth local frame $(E_i)$, the **connection coefficients** of $\nabla$ satisfy
>$$\begin{align}\Gamma_{k,i}^{l}g_{l,j} + \Gamma_{k,j}^{l}g_{i,l} &= E_k(g_{i,j}).\end{align}$$
>- If $V, W$ are *smooth vector fields* along any **smooth curve** $\gamma$, then $$\begin{align}D_{t}\left\langle  V\,,\,  W  \right\rangle &= \left\langle  D_tV\,,\, W   \right\rangle + \left\langle  V\,,\,D_{t}W    \right\rangle.\end{align}$$
>- If $V, W$ are **parallel vector fields** *along a smooth curve* $\gamma$ in $\mathcal{M}$, then $\left\langle  V\,,\, W   \right\rangle_{g}$ is **constant** *along* $\gamma$.
>- Given any smooth curve $\gamma$ in $\mathcal{M}$, every **parallel transport map** along $\gamma$ is a **linear isometry**. $$\lVert P_{t_{0},t_{1}}^{\gamma}(V) \rVert = \lVert V \rVert  $$
>-  Given any smooth curve $\gamma$ in $\mathcal{M}$, every **orthonormal basis** *at a point* of $\gamma$ can be **extended** to a **parallel orthonormal frame** along. 
> 
>![[parallel_orthonormal_frame.png]]

- [[Riemannian Metric and Riemannian Manifold]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Parallel Transport Algebraic Definitions]]
- [[Isometry and Isometric isomorphism]]
- [[Local and Global Frame for Tangent Bundle]]


>[!important] Corollary
>Suppose $(\mathcal{M}, g)$ is a *Riemannian* or *pseudo-Riemannian manifold* with or without boundary, $\nabla$ is a **metric connection** on $M$, and $\gamma: I \rightarrow M$ is a *smooth curve*.
>- $\lvert \gamma'(t) \rvert$ is **constant** *if and only if* the **covariant derivative** is **orthogonal** to **velocity field** of curve $\gamma$  $$D_t\gamma'(t) \perp \gamma'(t), \quad \forall t\in I$$
>- If $\gamma$ is a **geodesic**, then $\lvert \gamma'(t) \rvert$ is **constant**.
> 

- [[Geodesic in Riemannian Manifold]]
- [[Geodesic on Manifolds]]

## Submanifold

>[!important] Proposition
>If $\mathcal{M}$ is an **embedded** *Riemannian* or *pseudo-Riemannian* **submanifold** of $\mathbb{R}^n$ or $\mathbb{R}^{r \times s}$, the **tangential connection** on $\mathcal{M}$ is **compatible** with the **induced** Riemannian or pseudo-Riemannian **metric**.


- [[Embedded Submanifold]]




-----------
##  Recommended Notes and References

- [[Symmetric Connection]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Inner Product Space]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]] pp 118