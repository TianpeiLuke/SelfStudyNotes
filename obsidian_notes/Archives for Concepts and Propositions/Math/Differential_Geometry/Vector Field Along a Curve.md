---
tags:
  - concept
  - math/differential_geometry
keywords:
  - vector_field_along_curve
topics:
  - differential_geometry
name: Vector Field Along a Curve
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Vector Field Along a Curve

>[!important] Definition
>A parameterized curve $$\alpha: [0, l] \rightarrow \mathcal{S}$$ is the **restriction** to $[0,l]$ of a differentiable mapping of $(-\epsilon, l+\epsilon)$ into $\mathcal{S}$ for small $\epsilon>0$. 
>
>If $$\alpha(0) = p, \;\; \alpha(l) = q,$$ we say that $\alpha$ **joins** $p$ to $q$. $\alpha$ is **regular** if $$\dot{\alpha}(t)\neq 0, \;t\in [0,l].$$

- [[Parameterized Curve on Manifold]]
- [[Regular Point and Regular Value of Smooth Map]]
- [[Critical Point and Critical Value of Smooth Map]]

>[!important] Definition
>Let $\mathcal{S}$ be a smooth manifold. Denote $I= [0,l]$. Let $$\alpha: I\rightarrow \mathcal{S}$$ be a *parameterized curve* in $\mathcal{S}$. 
>
>A **vector field** $w$ **along** $\alpha$ is a correspondence that assigns to each $t\in I$ a vector 
>$$
> \begin{align*}
> V(t) \in T_{\alpha(t)}\mathcal{S}.
> \end{align*}
>$$ 
>
>- The vector field is **differentiable** at $t_{0}\in I$ if for some *parameterization* $x(u,v)$ in $\alpha(t_{0})$ the components $V^{u}(t), V^{v}(t)$ of $$V(t) = V^{u}(t)\,x_{u} + V^{v}(t)\,x_{v}$$ are *differentiable* functions of $t$ at $t_{0}$. 
>- $V$ is **differentiable** in $I$ if it is *differentiable* for *every* $t\in I$.

- [[Vector Field on Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Coordinate Representation of Vector Field on Manifold]]





## Explanation





-----------
##  Recommended Notes and References


- [[Coordinate Chart]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Tangent Space Definition and Development]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Smooth Manifold]]


- [[Introduction to Riemannian Manifolds by Lee]]
- [[Introduction to Smooth Manifolds by Lee]]