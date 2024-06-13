---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_covector_field
topics:
  - differential_geometry
name: Smooth Covector Field on Manifold
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Smooth Covector Field on Manifold

>[!important] Definition
>If $M$ is a smooth manifold with or without boundary. 
>
>A **smooth (local or global) covector field**  is a smooth (local or global) section of cotangent bundle $T^{*}M$

- [[Smooth Section of Vector Bundle]]
- [[Cotangent Bundle]]


## Coordinate Representation

- [[Coordinate Representation of Covector Field on Manifold]]

>[!info]
>If $\omega$ is a **(rough) covector field** and $X$ is a **vector field** on $M$, then we can form a
> function $\omega(X): M \rightarrow \mathbb{R}$ by
> $$
> \begin{align*}
> \omega(X)(p) &= \omega_{p}(X_{p}), \quad p \in M.
> \end{align*}
>$$ 

>[!info]
>If we write $$\omega = \omega_i\,\lambda^i$$ and $$X = X^j \frac{\partial }{\partial x^{j}}$$ in terms of **local coordinates**, then $\omega(X)$ has the **local coordinate representation** $$\omega(X) = \omega_i\, X^i.$$

## Smoothness Criteria

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, and let $\omega: M \rightarrow T^{*}M$ be a *rough covector field*. The following are **equivalent**:
>
>- $\omega$ is **smooth**.
>- In **every** **smooth coordinate chart**, the **component functions** of $\omega$ are **smooth**.
>- Each point of $M$ is contained in **some** *coordinate chart* in which $\omega$ has **smooth component functions**.
>- For **every smooth vector field** $X \in \mathfrak{X}(M)$, the function $\omega(X)$ is **smooth** on $M$.
>- For **every open subset** $U \subseteq M$ and **every smooth vector field** $X$ on $U$, the function $\omega(X): U \rightarrow \mathbb{R}$ is **smooth** on $U$.



## Examples










-----------
##  Recommended Notes and References

- [[Smooth Section of Vector Bundle]]


- [[Introduction to Smooth Manifolds by Lee]]