---
tags:
  - concept
  - math/differential_geometry
keywords:
  - sharp_operator
  - gradient_smooth_map
topics:
  - differential_geometry
name: Gradient of Smooth Map
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Gradient of Smooth Map

![[Sharp Operator and Raise Index of Covector Field#^29941b]]


>[!important] Definition
>If $g$ is a *Riemannian metric* on $M$ and $f: M \rightarrow \mathbb{R}$ is a *smooth function*, the **gradient** of $f$ is *the vector field*.
>
>That is, the **gradient operator** $\text{grad}: \mathcal{C}^{\infty}(M)\to \mathfrak{X}(M)$ is defined as 
>$$
> \begin{align*}
> \text{grad }f &= (df)^{\sharp} := \widehat{g}^{-1}(df)
> \end{align*} 
>$$  
>obtained from the *differential* of $f$ by *raising an index*. 
>
>It is also denoted as $\nabla f$.

- [[Differential of a Smooth Map at Point]]
- [[Vector Field on Manifold]]
- [[Sharp Operator and Raise Index of Covector Field]]
- [[Einstein Summation Convention]]

>[!info]
>By definition, for $X \in \mathfrak{X}(M)$, $f\in \mathcal{C}^{\infty}(M)$, then 
>$$
>\left\langle \text{grad }f, X \right\rangle_{g} := \hat{g}\left(\text{grad }f \right)(X) = df(X) = Xf
>$$

>[!important] Alternative Definition
>The **gradient operator** $\text{grad}: \mathcal{C}^{\infty}(M)\to \mathfrak{X}(M)$ is the *unique operator* that satisfies the equation
>$$
>\left\langle \text{grad }f, X \right\rangle_{g} = df(X)
>$$
>for all vector fields $X \in \mathfrak{X}(M)$.
>
>Or, equivalently,
>$$
>\left\langle \text{grad }f, \cdot \right\rangle_{g} = df
>$$

## Explanation

>[!info]
>- The *differential* $df \in \mathfrak{X}^{*}(M)$ is a **linear functional** on $T_{p}M$,  
>- The *gradient*  $\text{grad}\, f$ is the **dual correspondence** of *differential* $df$ in $\mathfrak{X}(M)$ for the linear functional. 
>
>Similar result is seen in [[Riesz Representation Theorem]], where $h \mapsto x_{h}$
>$$
>h = \left\langle \cdot, x_{h} \right\rangle_{\mathcal{H}}
>$$




-----------
##  Recommended Notes and References

- [[Vector Field on Manifold]]
- [[Differential of a Smooth Map at Point]]


- [[Tangent-Cotangent Isomorphism in Riemannian Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]



- [[Introduction to Riemannian Manifolds by Lee]]