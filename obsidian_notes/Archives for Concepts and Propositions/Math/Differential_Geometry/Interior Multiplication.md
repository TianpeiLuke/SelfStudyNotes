---
tags:
  - concept
  - math/differential_geometry
keywords:
  - interior_multiplication
topics:
  - differential_geometry
name: Interior Multiplication
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Interior Multiplication

>[!important] Definition
>Let $V$ be a finite-dimensional vector space. For each $v \in V$, we define a *linear map* $$\iota_v: \Lambda^k(V^{*}) \rightarrow \Lambda^{k-1}(V^{*}),$$ called **interior multiplication** (**interior product**) *by* $v$, as follows:
>$$
> \begin{align*}
> (\iota_v\omega)(w_1,\ldots, w_{k-1}) &= \omega\left(v, w_1,\ldots, w_{k-1}\right).
> \end{align*}
>$$  
>
>In other words, $(\iota_v\omega)$ is obtained from $\omega$ by **inserting** $v$ **into the first slot**. 

>[!info]
 >By convention, we interpret $(\iota_v\omega)$ to be **zero** when $\omega$ is a **$0$-covector** (i.e., a **number**). 
 
 >[!important] Definition
 >Another common notation is
 >$$
> \begin{align*}
> v \mathbin{\lrcorner } \omega &= (\iota_v\omega).
> \end{align*}
>$$ 
> This is often read ""**$v$ into $\omega$**."

>[!info]
>$$
>(v \mathbin{\lrcorner } \omega)(x_{1} \,{,}\ldots{,}\, x_{k-1}) := \omega(v, x_{1} \,{,}\ldots{,}\, x_{k-1})
>$$

>[!important]
>**Interior multiplication** also extends naturally to *vector fields* and *differential forms*, simply by letting it act *pointwise*: 
>
>If $X\in \mathfrak{X}(M)$ and $\omega \in \Omega^k(M)$, define a $(k-1)$-form $X \mathbin{\lrcorner } \omega = \iota_{X}\omega$ by
>$$
> \begin{align*}
> (X \mathbin{\lrcorner }  \omega)_p &= X_p \mathbin{\lrcorner } \omega_p.
> \end{align*}
>$$ 

## Explanation





-----------
##  Recommended Notes and References

- [[Exterior Forms]]
- [[Differential k-Form on Manifold]]


- [[Concepts and Theorems in Tensor Space]]



