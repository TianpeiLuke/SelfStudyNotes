---
tags:
  - concept
  - math/differential_geometry
keywords:
  - pullback_covector_fields
topics:
  - differential_geometry
name: Pullback of Covector Fields
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Pullback of Covector Fields


>[!important] Definition
>Let $F: M \rightarrow N$ be a *smooth map* between smooth manifolds with or without boundary, and let $p \in M$ be *arbitrary*. 
>
>The differential $dF_p: T_{p}M \rightarrow T_{F(p)}N$ yields a *dual linear map*
>$$
> \begin{align*}
> dF_{p}^{*}:  T_{F(p)}^{*}N \rightarrow T_{p}^{*}M,
> \end{align*}
>$$  
>called **the (pointwise) pullback by $F$ at $p$**, or **the cotangent map** of $F$. 
>
>Unraveling the definitions, we see that $dF_{p}^{*}$ is characterized by
>$$
> \begin{align*}
> dF_{p}^{*}(\omega)(v) &= \omega(dF_{p}(v)), \quad  \omega \in T_{F(p)}^{*}N, \; v \in T_{p}^{*}M.
> \end{align*}
>$$
>

- [[Differential of a Smooth Map at Point]]

>[!important]
>It is important to recognize that **the pullback** $dF_{p}^{*}$ is the **Banach Adjoint** of the linear map $dF_{p}$ 
>$$
>(T'f)(x) = f(T(x))
>$$

- [[Adjoint of Bounded Operator in Banach Space]]

>[!important] Definition
>Given a smooth map $F: M \rightarrow N$ and a *covector field* $\omega$ on $N$ , define a *rough covector field* $F^{\#}\omega$ on $M$, called **the pullback of $\omega$ by $F$**, by
>$$
> \begin{align*}
> (F^{*}\omega)_p &= dF_{p}^{*}\left(\omega_{F(p)}\right)
> \end{align*} 
>$$  
>We also denote **the pullback of $\omega$ by $F$** as $F^{\#}\omega$, or $F^{*}\omega$.

>[!info]
>The "pullback" suggests that it *defines a covector field* in the **domain** of function $F$ via **pulling back** a *covector field* in the **codomain** of function $F$

>[!important]
>The *pullback of covector field* **acts on a tangent vector** $v \in T_{p}M$ by
>$$
> \begin{align*}
> (F^{*}\omega)_{p}(v) = dF^{*}_{p}(\omega_{F(p)})(v) = \omega_{F(p)}(dF_{p}(v)) 
> \end{align*}
>$$ 


## Explanation

>[!info]
>- $F_{*}X$ **_pushes_** a *vector field* in **domain** of function $F$ **_forward_** to the **codomain** of $F$.
>- $F^{*}\omega$ **_pulls_** a *covector field* from **codomain** of function $F$ **back** to the **domain** of $F$


>[!info]
>- the **pushforward of a vector field by $F$**, $F_{*}X$, is **only uniquely defined** for **diffeomorphism** $F$,
>- the **pullback of a covector field by $F$**, $F^{*}\omega$, is **always unique**.    


>[!info]
>Recall the pushforward of vector fields [[Pushforward of Vector Fields]], there is **no special requirement for pullback function**, such as the diffeomorphism for pushforward.

>[!info]
>**Pullback** is an operator that is more "natural" to the definition of covector field as it represent **the change of variables** operation. 



>[!important] Proposition
>Let $F: M \rightarrow N$ be a smooth map between smooth manifolds with or without boundary.
> 
> Suppose $u$ is a **continuous** real-valued function on $N$, and $\omega$ is a **covector field** on $N$. 
> 
> Then
> $$
> \begin{align}
> F^{*}(u\, \omega) &= (u \circ F) F^{*}\omega 
> \end{align}
>$$  
>If in addition $u$ is **smooth**, then
>$$
> \begin{align}
> F^{*}du  &=  d(u \circ F) 
> \end{align}
> $$








-----------
##  Recommended Notes and References


- [[Differential of a Smooth Map at Point]]
- [[Smooth Map]]
- [[Pullback by Bounded Operator in Banach Space]]
  
- [[Space of all Smooth Covector Fields on a Manifold]]
- [[Smooth Covector Field on Manifold]]
- [[Covector Field on Manifold]]





- [[Introduction to Smooth Manifolds by Lee]]