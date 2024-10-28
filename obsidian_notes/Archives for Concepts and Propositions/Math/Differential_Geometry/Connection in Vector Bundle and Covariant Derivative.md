---
tags:
  - concept
  - math/differential_geometry
keywords:
  - connection_vector_bundle
  - covariant_derivative
topics:
  - differential_geometry
name: Connection on Vector Bundle
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Connection on Vector Bundle or *Covariant Derivative*

>[!important] Definition
>Let $\pi: E \rightarrow M$ be a **smooth vector bundle** over *a smooth manifold* $M$ with or without boundary, and let $\Gamma(E)$ denote *the space of* *smooth sections* of $E$. 
>
>A **connection** in $E$ is a map 
>$$
> \begin{align*}
> \nabla: \mathfrak{X}(M) \times \Gamma(E) \rightarrow \Gamma(E),
> \end{align*} 
>$$ 
> written $(X, Y) \mapsto  \nabla_{X}Y$, satisfying the following **properties**:
>
>- $\nabla_{X}Y$ is **linear** *over* $\mathcal{C}^{\infty}(M)$ **in** $X$: for $f_1, f_2 \in \mathcal{C}^{\infty}(M)$ and $X_1, X_2  \in \mathfrak{X}(M)$,
> $$ 
> \begin{align*}
> \nabla_{\left(f_1\,X_1 + f_2\,X_2\right)}Y &= f_1\,\nabla_{X_{1}}Y + f_2\,\nabla_{X_{2}}Y
> \end{align*}
>$$ 
>- $\nabla_{X}Y$ is **linear** *over* $\mathbb{R}$ **in** $Y$: for $a_1, a_2 \in \mathbb{R}$ and $Y_1, Y_2  \in \Gamma(E)$,
>$$  
> \begin{align*}
> \nabla_{X}\left(a_1\,Y_1 + a_2\,Y_2\right) &= a_1\,\nabla_{X}Y_{1} + a_2\,\nabla_{X}Y_{2}
> \end{align*}
>$$ 
>- $\nabla$ *satisfies* the following **product rule (Lebnitz rule)**: for $f \in \mathcal{C}^{\infty}(M)$,
>$$ 
> \begin{align*}
> \nabla_{X}(fY) &= f\,\nabla_{X}Y + (Xf)\,Y
> \end{align*}
>$$ 
>
>The symbol $\nabla$ is read "**del**" or "**nabla**," and $\nabla_{X}Y$ is called **the covariant derivative** of $Y$ **in the direction** $X$.

^94b423

- [[Tangent Bundle]]
- [[Vector Bundle]]
- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Space of all Smooth Vector Fields on a Manifold]]



## Explanation


## Covariant Derivative along Smooth Curve

- [[Covariant Derivative Along a Curve]]


-----------
##  Recommended Notes and References

- [[Tangent Bundle]]
- [[Vector Bundle]]
- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Space of all Smooth Vector Fields on a Manifold]]

- [[Introduction to Riemannian Manifolds by Lee]] pp 85 - 100