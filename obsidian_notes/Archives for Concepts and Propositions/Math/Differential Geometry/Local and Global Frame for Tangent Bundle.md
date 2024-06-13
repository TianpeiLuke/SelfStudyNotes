---
tags:
  - concept
  - math/differential_geometry
keywords:
  - local_frame
  - global_frame
topics:
  - differential_geometry
name: Local and Global Frame in Space of Vector Fields
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Local and Global Frame in Space of Vector Fields

>[!info]
>$\mathfrak{X}(M)$ is a **vector space** under *pointwise addition* and *scalar multiplication*
>- For any $a, b \in \mathbb{R}$ and any $X, Y \in \mathfrak{X}(M)$,
>$$  
> \begin{align*}
> (a\,X + b\,Y)_{p} &= a\,X_{p} + b\,Y_{p}.
> \end{align*}
>$$ 
>- The **zero element** of this vector space is the **zero vector field**, whose value at each $p \in M$ is $0 \in T_{p}M$.
>- In addition, *smooth vector fields* can be **multiplied** by **smooth real-valued functions**: 
>  if $f \in \mathcal{C}^{\infty}(M)$ and $X \in \mathfrak{X}(M)$, we define $fX: M \rightarrow TM$ by
> $$ 
> \begin{align*}
> (fX)_p &= f(p)\, X_p.
> \end{align*}
>$$   

- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Vector Space over a Field]]
- [[Smooth Vector Field on Manifold]]

>[!info]
>Coordinate vector fields in a smooth chart provide a convenient way of representing vector fields, because *their values form a basis* for *the tangent space* **at each point.** However, they are not the only choices. 

>[!important] Definition
>Suppose $M$ is a smooth $n$-manifold with or without boundary. 
>
>An *ordered $k$-tuple* $(X_1, \ldots, X_k)$ of *vector fields* defined on some subset $A \subseteq M$ is said to be **linearly independent** if $$(X_1|_{p}, \ldots, X_k|_{p})$$ is a *linearly independent* $k$-tuple in $T_{p}M$ *for each* $p \in A$.
>
>It is said to **span the tangent bundle** if the $k$-tuple $(X_1|_{p},\ldots,X_k|_{p})$ *spans* $T_{p}M$ *at each* $p \in A$. 

- [[Basis of Vector Space]]
- [[Linear Independence]]

>[!important] Definition
>A **local frame** for $M$ is *an ordered* $n$-tuple of *vector fields* $(E_1,\ldots,E_n)$ defined on an *open subset* $U \subseteq M$ that is **linearly independent** and **spans the tangent bundle**; 
>
>thus the vectors $(E_1|_{p},\ldots,E_n|_{p})$ **form a basis** for $T_{p}M$ *at each* $p \in U$.

>[!important] Definition
>- $(E_1,\ldots,E_n)$ is called a **global frame** if $U = M$, and
>- a **smooth frame** if each of the vector fields $E_i$ is **smooth**.

>[!info]
>We often use the shorthand notation $(E_i)$ to denote *a frame* $(E_1,\ldots,E_n)$.


## Explanation


## Example

>[!example]
>The **standard coordinate vector fields** $$\left( \frac{\partial }{ \partial x^{i}} \right)$$ form a **smooth global frame** for $\mathbb{R}^n$.

>[!example]
 If $(U, (x^i))$ is any smooth coordinate chart for a smooth manifold $M$ (possibly with boundary), then the **coordinate vector fields** form a **smooth local frame** $$\left( \frac{\partial }{ \partial x^{i}} \right)$$  on $U$, called a **coordinate frame**. 
 >
 >*Every point* of $M$ is *in the domain* of such a local frame.

>[!example]
>The **angle coordinate vector field** $$\frac{d}{d\theta}$$ constitutes a **smooth global frame** for the **circle** $\mathbb{S}^1$.

>[!example]
>The $n$-tuple of vector fields $$\left(\frac{d}{d\theta^{i}}\right)$$ is a **smooth global frame** for the **$n$-torus** $\mathbb{T}^{n}$.










-----------
##  Recommended Notes and References


- [[Vector Field on Manifold]]
- [[Tangent Bundle]]
- [[Derivation of Smooth Map at point and Tangent Vector]]

- [[Introduction to Smooth Manifolds by Lee]]