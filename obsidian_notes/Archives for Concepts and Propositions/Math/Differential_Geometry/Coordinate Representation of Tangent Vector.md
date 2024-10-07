---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_coordinate
topics:
  - differential_geometry
name: Coordinates Representation of the Derivation
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Coordinates Representation of Derivation (Tangent Vector)


### The Basis Vector of Tangent Space


>[!important] Definition
>The vectors $$\frac{\partial}{\partial x^i}\Bigr|_{p}$$ 
> are called the **coordinate vectors** *at $p$* *associated with the given coordinate system*.

- [[Basis of Vector Space]]
### Coordinate Representation of Tangent Vector

>[!important] Definition
>A **tangent vector** $v \in T_{p}M$ can be written **uniquely** as *a linear combination*
>$$
> \begin{align}
> v&=v^{i} \frac{\partial}{\partial x^i}\Bigr|_{p}
> \end{align} 
>$$ 
>where we use the *Einstein summation convention* as usual. 

- [[Einstein Summation Convention]]

### The Coordinate System of Tangent Space 


>[!important] Definition
>The *ordered basis* $$\left(\frac{\partial}{\partial x^i}\Bigr|_{p}\right)$$  is called a **coordinate basis** for $T_{p}M$, and the numbers $$(v^1, \ldots, v^n)$$ are called the **components** of $v$ *with respect to the coordinate basis.*



## Development of the Basis of Tangent Space


### Isomorphism between Tangent Space of Manifold and Tangent Space of Euclidean Space

>[!info]
>First, suppose $M$ is a smooth manifold (without boundary), and let $(U, \varphi)$ be a smooth coordinate chart on $M$. 
>
>Then $\varphi$ is, in particular, a **diffeomorphism** from $U$ to an *open subset* $\widehat{U} \subseteq \mathbb{R}^n$. 

- [[Smooth Manifold]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Diffeomorphism]]


>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, let $U \subseteq M$ be an **open subset**, and let $$\iota: U \xhookrightarrow{} M$$ be the **inclusion map**. 
>
>For every $p \in U$, the **differential** $$d\iota_{p}: T_{p}U \rightarrow T_{p}M$$ is an **isomorphism**.

>[!info]
> Combining Propositions above  and the following property of **differential of diffeomorphism**
>>[!important]
>>If $F$ is a **diffeomorphism**, then $dF_{p}: T_{p}M \rightarrow T_{F(p)}N$ is an **isomorphism**, and
>>$(dF_{p})^{-1} = d(F^{-1})_{F(p)}$ 
> 
> we see that $$d\varphi_{p}: T_{p}M \rightarrow T_{\varphi(p)}\mathbb{R}^n$$ is an **isomorphism**.

### Basis Vector as Derivations on Tangent Space of Euclidean Space

Recall that 

>[!info] Proposition
>
> Let $a \in \mathbb{R}^n$.
> 1. For each geometric tangent vector $v_a \in \mathbb{R}_{a}^n$, the map $D_v|_a: \mathcal{C}^{\infty}(\mathbb{R}^n) \rightarrow \mathbb{R}$ defined by following 
> $$
> \begin{align}
> D_v|_a(f) &= D_{v}(f(a)) = \frac{d}{dt}\Big|_{t=0}f(a + t\,v).
> \end{align}
> $$
> is a *derivation* at a. $D_v|_a(f)$, called the **directional derivative** of $f$ *along vector* $v$ at point $a$. 
> 
> 2. The map $v_a \rightarrow D_v|_a$ is an **isomorphism** from $\mathbb{R}_{a}^n$ onto $T_{a}\mathbb{R}^n$.

 - [[Derivation of Smooth Map at point and Tangent Vector]]

>[!info]
>This leads to the following corollary

>[!important] Corollary
>For any $a \in \mathbb{R}^n$, the **$n$ derivations**
>$$
> \begin{align}
> \frac{\partial}{\partial x^1}\Bigr|_{a}, \ldots, \frac{\partial}{\partial x^n}\Bigr|_{a} \quad\text{defined by }\;\;\frac{\partial}{\partial x^i}\Bigr|_{a}(f) := \frac{\partial f}{\partial x^i}(a).
> \end{align}
>$$  
>form a  **basis** for $T_{a}\mathbb{R}^n$, which therefore has dimension $n$.
>
>Simply note that $$\frac{\partial}{\partial x^i}\Bigr|_{a} = D_{e_i}|_a.$$


>[!info]
>From the above corollary, we see that 
>$$
>\frac{\partial}{\partial x^1}\Bigr|_{\varphi(p)}, \ldots, \frac{\partial}{\partial x^n}\Bigr|_{\varphi(p)}
>$$
>form a **basis** for $T_{\varphi(p)}\mathbb{R}^n$.


### Basis Derivations on Tangent Space of Manifold


>[!info]
>Therefore, **the preimages** of *these vectors* under the **isomorphism** $d\varphi_p$ **form a basis** for $T_{p}M$.

>[!important]
> In keeping with our standard practice of **treating coordinate maps as identifications** whenever possible, we use the notation $$\frac{\partial}{\partial x^i}\big|_{p}$$  for these **vectors**, characterized by either of the **following expressions**:
> $$
> \begin{align}
> \frac{\partial}{\partial x^i}\Bigr|_{p} &:= (d\varphi_{p})^{-1}\left(\frac{\partial}{\partial x^i}\Bigr|_{\varphi(p)}\right)
> = d(\varphi^{-1})_{\varphi(p)}\left(\frac{\partial}{\partial x^i}\Bigr|_{\varphi(p)}\right) 
> \end{align}
>$$ 

>[!important]
>Unwinding the definitions, we see that $\frac{\partial}{\partial x^i}\big|_{p}$ **acts** on a function $f \in \mathcal{C}^{\infty}(U)$ by
>$$
> \begin{align*}
> \frac{\partial}{\partial x^i}\big|_{p}(f) &= \frac{\partial}{\partial x^i}\big|_{\varphi(p)}(f \circ \varphi^{-1}) =  \frac{\partial \widehat{f}}{\partial x^i}\big|_{\varphi(p)}
> \end{align*}
>$$  
>where $\widehat{f} = f \circ \varphi^{-1}$ is the **coordinate representation** of $f$, and $\widehat{p} = (p^1, \ldots, p^n) = \varphi(p)$ is the **coordinate representation** of $p$.

- [[Coordinate Representation of Smooth Map]]


>[!info]
>In other words,
>$$\frac{\partial}{\partial x^i}\big|_{p}$$ 
>is just the **derivation** that takes the *$i$-th partial derivative* of **the coordinate representation** of $f$ at (the coordinate representation of) $p$. 





-----------
##  Recommended Notes and References

- [[Derivation of Smooth Map at point and Tangent Vector]]

- [[Linear Independence]]
- [[Basis of Vector Space]]
- [[Vector Space over a Field]]


- [[Smooth Manifold]]
- [[Smooth Map]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Smooth Map between Smooth Manifolds]]


