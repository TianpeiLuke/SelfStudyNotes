---
tags:
  - concept
  - math/differential_geometry
keywords:
  - derivation_at_point
topics:
  - differential_geometry
name: Derivation at point
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Derivation at a point $a$ or *tangent vector*

>[!important] Definition on Euclidean Space
>If $a$ is a point of $\mathbb{R}^n$, a map $w: \mathcal{C}^{\infty}(\mathbb{R}^n) \rightarrow \mathbb{R}$ is called a **derivation at $a$** if it is *linear* over $\mathbb{R}$ and satisfies the following **product rule (Leibnitz rule)**:
>
> $$
> \begin{align}
> w(f\,g) &= f(a)\,w(g) + g(a)\,w(f), \quad  \forall\,f,g \in \mathcal{C}^{\infty}(\mathbb{R}^{n})  
> \end{align}
> $$

- [[Smooth Map]]

>[!important] Definition on Smooth Manifold
>Let $M$ be a *smooth manifold* with or without boundary, and let $p$ be a point of $M$. 
>
>A *linear map* $v: \mathcal{C}^{\infty}(M) \rightarrow \mathbb{R}$ is called a **derivation at p** if it satisfies the **Leibnitz rule**:
> $$
> \begin{align*}
> v(f\,g) &= f(a)\,v(g) + g(a)\,v(f), \quad \forall\,f,g \in \mathcal{C}^{\infty}(M)
> \end{align*}
> $$


- [[Smooth Function on Smooth Manifold]]
- [[Smooth Manifold]]

## Explanation

### Geometric Tangent Vector and Derivation Operator 

>[!info]
>An element in Euclidean space $(x^1, \ldots, x^n) \in \mathbb{R}^{n}$ has **two distinct roles**: 
> 
> 1. As a **point** in space, whose only *property* is its **location** $(x^1, \ldots, x^n)$;
> 2. As a **vector**, which are objects that have **magnitude** and **direction**, but whose *location is irrelevant.*

>[!info]
>A vector $x = x^i e_i$ (where $e_i$ denotes the $i$-th *standard basis vector*) can be visualized as an arrow with its *initial point anywhere* in $\mathbb{R}^n$; what is relevant from the vector point of view is *only **which direction** it points* and **how long** it is.


### Tangent Space

>[!info]
> Let $T_{a}\mathbb{R}^n$ denote the *set of all derivations* of $\mathcal{C}^{\infty}(\mathbb{R}^n)$ at $a$. 
> 
> Clearly, $T_{a}\mathbb{R}^n$  is a **vector space** under the operations
> $$
> \begin{align*}
> (w_1 + w_2)(f)  = w_1(f) + w_2(f), \quad (c\,w)(f) = c\,w(f).
> \end{align*}
> $$

>[!info]
>Note that by definition, a **derivation** $w \in T_{a}\mathbb{R}^n$ is a **linear functional** on $\mathcal{C}^{\infty}(\mathbb{R}^n)$. Thus $T_{p}\mathbb{R}^{n}$ is a *functional space*.

- [[Tangent Space Definition and Development]]

>[!info]
>Similar to Euclidean space, the derivation on smooth manifold $M$ is a **linear functional** on *smooth functions* on $M$.

- [[Smooth Function on Smooth Manifold]]

## Properties

>[!important] Proposition
> Suppose $M$ is a smooth manifold with or without boundary, $p \in M, v \in T_{p}M$, and $f, g \in \mathcal{C}^{\infty}(M)$. 
> 
>- If $f$ is a *constant function*, then $v(f) = 0$. 
>- If $f(p) = g(p) = 0$, then $v(f\,g) = 0$.

>[!info]
>The following shows that tangent vector **acts locally**.

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, $p \in M$, and $v \in T_{p}M$. 
>
>If $f, g \in \mathcal{C}^{\infty}(M)$ **agree on some neighborhood** of $p$, then $v(f) = v(g)$.

## Connection with Geometric Tangent Vector

>[!info]
>By definition of [[Tangent Space Definition and Development]], a derivation at $p$, $v\in T_{p}\mathcal{M}$, is also called a **tangent vector**. 
>
>That is, tangent vector is a **linear functional** on *smooth map*.

>[!info]
>The following proposition shows the one-to-one correspondence between **derivations** and the **geometric tangent vector**.

>[!important] Proposition
>
> Let $a \in \mathbb{R}^n$.
> 1. For each geometric tangent vector $v_a \in \mathbb{R}_{a}^n$, the map $D_v|_a: \mathcal{C}^{\infty}(\mathbb{R}^n) \rightarrow \mathbb{R}$ defined by following 
> $$
> \begin{align}
> D_v|_a(f) &= D_{v}(f(a)) = \frac{d}{dt}\Big|_{t=0}f(a + t\,v).
> \end{align}
> $$
> is a *derivation* at a. $D_v|_a(f)$ is called the **directional derivative** of $f$ *along vector* $v$ at point $a$. 
> 
> 2. The map $v_a \rightarrow D_v|_a$ is an **isomorphism** from $\mathbb{R}_{a}^n$ onto $T_{a}\mathbb{R}^n$.

## Coordinate Representation of Tangent Vector

- [[Coordinate Representation of Tangent Vector]]



-----------
##  Recommended Notes and References

- [[Introduction to Smooth Manifolds by Lee]]