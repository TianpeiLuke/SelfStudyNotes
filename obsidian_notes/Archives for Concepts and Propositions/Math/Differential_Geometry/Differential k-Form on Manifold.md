---
tags:
  - concept
  - math/differential_geometry
keywords:
  - differential_k_form
topics:
  - differential_geometry
name: Differential k Form on Manifold
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Differential $k$-Form or $k$-form

>[!important] Definition
>A *section* of $\Lambda^k(T^{*}M)$ is called a **differential $k$-form**, or just a **$k$-form**;  this is a *(continuous) tensor field* whose value at *each point* is an *alternating tensor*. 
>
>The integer $k$ is called the **degree** of *the form*. 

>[!important] Definition
>We denote the *vector space* of **smooth $k$-forms** by
>$$
> \begin{align*}
> \Omega^{k}(M) &= \Gamma \left(\Lambda^k(T^{*}M)\right).
> \end{align*}
>$$ 

- [[Tensor Field on Manifold]]
- [[Vector Bundle of Covariant k-Tensor]]
- [[Alternating Tensor]]

## Explanation

>[!info]
>Differential $k$-form is an **alternating k-covector field**, whose *value* at each point $p$ is a **$k$-covector (exterior form)** in
>$$
> \text{Alt}\left(\underbrace{T_{p}^{*}M \otimes \ldots \otimes T_{p}^{*}M}_{k}\right)
>$$

- [[Exterior Forms]]

>[!info]
>The *wedge product* of **two differential forms** is defined *pointwise*: 
>$$(\omega \wedge \eta)_p = \omega_p \wedge \eta_p.$$ 
>
>Thus, *the wedge product* of a **$k$**-form with an **$l$**-form is a **$(k +l)$**-form. 
>
>If $f$ is a $0$-form (i.e. a **smooth function**) and $\omega$ is a $k$-form, we interpret the wedge product  $f\wedge \omega$ to mean the **ordinary product** $f\omega$.





-----------
##  Recommended Notes and References

- [[Vector Bundle of all Exterior Forms on Manifold]]
- [[Exterior Forms]]

- [[Differential as Covector Field]]

- [[Smooth Section of Vector Bundle]]
- [[Section of Vector Bundle]]

- [[Introduction to Smooth Manifolds by Lee]]