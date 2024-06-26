---
tags:
  - concept
  - math/differential_geometry
keywords:
  - space_vector_field
topics:
  - differential_geometry
name: The Space of all Smooth Vector Fields on a Manifold
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: The Space of all Vector Fields on a Manifold

>[!important] Definition
>If $M$ is a smooth manifold with or without boundary, it is standard to use the notation $\mathfrak{X}(M)$ to denote **the set of all smooth vector fields on $M$**. 

>[!important]
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

- [[Vector Space over a Field]]
- [[Smooth Vector Field on Manifold]]




## Explanation


>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary.
> 
> - If $X$ and $Y$ are *smooth vector fields* on $M$ and $f,g \in \mathcal{C}^{\infty}(M)$, then $fX + gY$ is a *smooth vector field*.
> - $\mathfrak{X}(M)$ is a **module** *over the* **ring** $\mathcal{C}^{\infty}(M)$.

- [[Left Module over Ring]]








-----------
##  Recommended Notes and References

- [[Space of all Smooth Sections of Vector Bundle]]

- [[Vector Field on Manifold]]
- [[Tangent Bundle]]


- [[Introduction to Smooth Manifolds by Lee]]