---
tags:
  - concept
  - math/differential_geometry
keywords:
  - pushforward_vector_field
topics:
  - differential_geometry
name: Pushforward of Vector Fields
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Pushforward of Vector Fields


>[!important] Definition
>Suppose $M$ and $N$ are smooth manifolds with or without boundary, and $F: M \rightarrow N$ is a **diffeomorphism**. 
>
>For every $X \in \mathfrak{X}(M)$, there is a **unique** *smooth vector field* $Y$ on $N$ that is **$F$-related to $X$**. 
>
>We denote the *unique vector field* that is *$F$-related* to $X$ by $F_{*}X$, and call it the **pushforward of $X$ by $F$**. 
>
>And $F_{*}X$ is defined explicitly by the formula
>$$
> \begin{align}
> (F_{*}X)_{q} &= dF_{F^{-1}(q)}(X_{F^{-1}(q)}),\quad \forall q\in N. 
> \end{align} 
>$$ 

- [[Smooth Maps on Space of Vector Fields]]
- [[Diffeomorphism]]
- [[Smooth Vector Field on Manifold]]

>[!info]
>As long as the inverse map $F^{-1}$ can be *computed explicitly*, the **pushforward** of a vector field can be computed directly from this formula. 
>
>Note that sometimes the **pushforward** of $X$ is denoted as $F_{\#}X$.



## Explanation

>[!info]
>Recall the **pushforward of measure** $\mathcal{P}$ by function $X$ as
>$$
>(X_{*}\mathcal{P})(B) := \mathcal{P}\{\omega: X(\omega) \in B  \} := \mathcal{P}\circ X^{-1}(B), \quad \forall B \in \mathscr{F}
>$$

- [[Push-forward Measure and Push-forward Operator]]


>[!info] Proposition
>Suppose $M$ and $N$ are smooth manifolds with or without boundary, and $F: M \rightarrow N$ is a **diffeomorphism**. 
>
>For every $X \in \mathfrak{X}(M)$, there is a **unique** *smooth vector field* on $N$ that is **$F$-related** to $X$.

>[!important] Corollary
>Suppose $F: M \rightarrow N$ is a **diffeomorphism** and $X \in \mathfrak{X}(M)$.  For any $f \in \mathcal{C}^{\infty}(N)$, 
>$$
> \begin{align*}
> (F_{*}X\,f) \circ F &= X(f \circ F)
> \end{align*}
>$$ 






-----------
##  Recommended Notes and References

- [[Diffeomorphism]]
- [[Differential of a Smooth Map at Point]]
- [[Smooth Map between Euclidean Spaces]]
  
  
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field on Manifold]]


- [[Vector Space over a Field]]
- [[Push-forward Measure and Push-forward Operator]]

- [[Introduction to Smooth Manifolds by Lee]]