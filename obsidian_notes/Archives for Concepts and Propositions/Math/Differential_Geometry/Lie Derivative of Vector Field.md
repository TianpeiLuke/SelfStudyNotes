---
tags:
  - concept
  - math/differential_geometry
keywords:
  - lie_derivative_vector_field
topics:
  - differential_geometry
name: Lie Derivative of Vector Field
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Lie Derivative of Vector Field

>[!important] Definition
>Suppose $M$ is a *smooth manifold*, $V$ is a *smooth vector field* on $M$; and $\theta$ is the **flow of $V$**. 
>
>For any smooth vector field $W$ on $M$, define a *rough vector field* on $M$, denoted by  **$\mathscr{L}_{V}\,W$** and called **the Lie derivative of $W$** *with respect to* $V$, by
>$$ 
> \begin{align}
> \left(\mathscr{L}_{V}\,W\right)_{p} &= \lim_{t\rightarrow 0}\frac{ d(\theta_{-t})_{\theta_{t}(p)}\left(W_{\theta_t(p)}\right)   - W_{p}}{t} \\
> &= \frac{d}{dt}\Bigr|_{t=0} d\left(\theta_{-t}\right)_{\theta_{t}(p)}\left(W_{\theta_t(p)}\right)  \nonumber,
> \end{align}
>$$ 
> provided the derivative exists. 


![[lie_derivatives.png]]


>[!important]
> For small $t \neq 0$, at least the **difference quotient** makes sense: 
> - $\theta_t$ is defined in a neighborhood of $p$, and 
> - $\theta_{-t}$ is the **inverse of** $\theta_t$, 
>
>- so both $$d(\theta_{-t})_{\theta_{t}(p)}\left(W_{\theta_t(p)}\right)$$ and $W_p$ are elements of $T_{p}M$.

- [[Smooth Vector Field on Manifold]]
- [[Local Flow on Smooth Manifold]]
- [[Integral Curve of Vector Field]]


## Explanation

![[Covariant Derivative from Parallel Transport#^6bab4a]]


- [[Covariant Derivative from Parallel Transport]]
- [[Bregman Divergence]]


## Relation with Lie Bracket

>[!important] Theorem
>If $M$ is a **smooth manifold** and $V, W \in \mathfrak{X}(M)$, then $$\mathscr{L}_{V}\,W = [V, W].$$

- [[Lie Bracket of Vector Fields]]


>[!important]
>This theorem allows us to extend the definition of the **Lie derivative** to arbitrary **smooth vector fields** on a smooth manifold $M$ **with boundary**. 
>
>Given $V, W \in \mathfrak{X}(M)$ we define $$(\mathscr{L}_{V}\,W)_{p}$$ for $p \in \partial M$ by **embedding** $M$ in a smooth manifold $\widetilde{M}$ **without boundary** (such as the double of $M$), **extending** $V$ and $W$ to smooth vector fields on $\widetilde{M}$, and *computing the Lie derivative there*. 
>
>By virtue of the preceding theorem,
>$$(\mathscr{L}_{V}\,W)_{p} = [V, W]_p$$ 
>is independent of the choice of extension.


## Properties

>[!important] Proposition
>Suppose $M$ is a smooth manifold with or without boundary, and $V, W, X \in \mathfrak{X}(M)$.
>
>- **Anti-symmetric** $$\mathscr{L}_{V}\,W = -\mathscr{L}_{W}\,V.$$
>- **Lie Derivative of Lie Bracket (Leibnitz rule)** $$\mathscr{L}_{V}\,[W,\, X] =  [\mathscr{L}_{V}\,W, \,X] + [W,\, \mathscr{L}_{V}\,X].$$
>- **Lie Derivative with respect to Lie Bracket** $$\mathscr{L}_{[V, W]}\,X = \mathscr{L}_{V}\mathscr{L}_{W}\,X - \mathscr{L}_{W}\mathscr{L}_{V}\,X.$$
>- **Leibnitz rule for smooth map**  If $g \in \mathcal{C}^{\infty}(M)$, then $$\mathscr{L}_{V}\,(gW) = (Vg)\,W + g\,\mathscr{L}_{V}\,W.$$
>- **Pushforward of Lie Derivative** If $F: M \rightarrow N$ is a *diffeomorphism*, then $$F_{*}(\mathscr{L}_{V}\,X) = \mathscr{L}_{F_{*}V}\,F_{*}X.$$
>

>[!info]
>Compare to the property of 
>- **Exterior differentiation**: [[Exterior Derivatives of Differential Form#Existence and Uniqueness of Exterior Derivative]]
>- **Covariant Derivative**:  [[Connection in Vector Bundle and Covariant Derivative]]

- [[Exterior Derivatives of Differential Form]]
- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Affine Connection on Tangent Bundle]]




-----------
##  Recommended Notes and References


- [[Local Flow on Smooth Manifold]]
- [[Integral Curve of Vector Field]]
- [[Smooth Vector Field on Manifold]]




- [[Introduction to Smooth Manifolds by Lee]] pp 228 - 230
- [[Introduction to Riemannian Manifolds by Lee]]
