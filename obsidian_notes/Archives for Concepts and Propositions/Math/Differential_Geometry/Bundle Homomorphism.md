---
tags:
  - concept
  - math/differential_geometry
keywords:
  - bundle_homomorphism
topics:
  - differential_geometry
name: Bundle Homomorphism
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Bundle Homomorphism


>[!important] Definition
>If $\pi: E \rightarrow M$ and $\pi': E' \rightarrow M'$ are *vector bundles*, a *continuous map* $F: E \rightarrow E'$ is called a **bundle homomorphism** if there exists a map $f: M \rightarrow M'$ satisfying $$\pi' \circ F = f \circ \pi,$$
>$$
>\begin{CD}
> E @>F>> E'\\ 
>@VV\pi V @VV\pi' V\\ 
>M @>f>> M'
>\end{CD}
>$$ 
>with the property that for each $p \in M$, the *restricted map* $$F|_{E_{p}}: E_p \rightarrow E'_{f(p)}$$ is **linear**. 
>
>The **relationship** *between $F$ and $f$* is expressed by saying that **$F$ covers $f$**.

- [[Vector Bundle]]
- [[Continuous Function]]


>[!important]
>By definition, a **bundle homomorphism** is **not necessary bijective**, unlike the normal *homemorphism* definition.

>[!important] Definition
>A **bundle homomorphism over $M$** is a *bundle homomorphism* **covering the identity map** of $M$; or in other words, a *continuous* map $F: E \rightarrow E'$ such that
>$$
>\begin{CD}
> E @>F>> E'\\ 
>@VV\pi V @VV\pi' V\\ 
>M @= M
>\end{CD}
>$$ 
>and whose *restriction to each fiber* is **linear**. 

>[!important] Definition
>If there exists a *bundle homomorphism* $F: E \rightarrow E'$ over $M$ that is also a **(smooth) bundle isomorphism**, then we say that $E$ and $E'$ are **(smoothly) isomorphic** over $M$. 



### Riemannian Manifold


>[!important] Definition
>Given a Riemannian metric $g$ on M, we define a **bundle homomorphism** $\widehat{g}: TM \rightarrow T^{*}M$ by setting
>$$
> \begin{align*}
> \widehat{g}(v)(w) &= g_{p}(v, w)
> \end{align*}
>$$  
>for all $p \in M$ and $v, w \in T_{p}M$.

^d28d96

- [[Riemannian Metric and Riemannian Manifold]]
- [[Tangent Bundle]]

>[!info]
>Consider the [[Riesz Representation Theorem]],  there exists an *isomorphism* $\hat{g}: \mathcal{H} \to \mathcal{H}^{*}$ such that
>$$
>\hat{g}: h \mapsto f_{h} \implies \hat{g}(h)(x) := \left\langle  x, h  \right\rangle
>$$


## Explanation





-----------
##  Recommended Notes and References

- [[Riemannian Metric and Riemannian Manifold]]

- [[Vector Bundle]]

- [[Continuous Function]]
- [[Topology of Set]]



- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]