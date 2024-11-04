---
tags:
  - concept
  - math/information_geometry
  - math/riemannian_geometry
keywords:
  - alpha_connection
topics:
  - riemannian_geometry
  - information_geometry
name: alpha-Connection on Statistical Manifold
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: $\alpha$-Connection on Statistical Manifold

![[Statistical Manifold as Parametric Family#^646891]]

- [[Statistical Manifold as Parametric Family]]

![[Christoffel Symbols#^ce4cd0]]
![[Christoffel Symbols#^587512]]

>[!important] Definition
>Let $\mathcal{S}$ be a $n$-dimensional *statistical manifold* with *parameterization* $\theta\in \Theta$. 
>- Denote $\ell_{\theta} := \log p_{\theta}$ as the *log-likelihood function*.
>
>The **$\alpha$-connections** $$\nabla^{(\alpha)}: \mathfrak{X}(\mathcal{S}) \times \mathfrak{X}(\mathcal{S}) \rightarrow \mathfrak{X}(\mathcal{S})$$ is *a family of affine connections* on the tangent bundle $T\mathcal{S}$, for $\alpha \in [-1, 1].$
>
>- The **coefficient** or the **Christoffel symbol** of the **$\alpha$-connection** under the *Fisher metric* is formulated as
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(\alpha)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} + \frac{1 - \alpha}{2}  \frac{\partial}{ \partial \theta^{i} }\ell_{\theta}\,\frac{\partial}{ \partial \theta^{j} }\ell_{\theta}\right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n
> \end{align}
>$$ 
> where
> $$
> \begin{align*}
> \Gamma_{i,j; k}^{(\alpha)} &:= \left\langle \nabla^{(\alpha)}_{\partial_i}{\partial_j}\,,\, \partial_k \right\rangle_{g},
> \end{align*}
>$$ 
> where $g_{i,j} = \left\langle \partial_{i} \ell \,,\, \partial_{j} \ell \right\rangle_p$ is the *Fisher metric*.

^24ddaa

- [[Affine Connection on Tangent Bundle]]
- [[Christoffel Symbols]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]
- [[Log-Likelihood Score Function]]
- [[Tangent Bundle]]
- [[Riemannian Metric and Riemannian Manifold]]

### Riemannian Connection

>[!important] Theorem
>The **$0$-connection** is the **Riemannian connection** with respect to **Fisher metric**.
>
>$$
>\begin{align*}
>\partial_{k}g_{i,j} &= \mathbb{E}_{ \theta }\left[  (\partial_{k}\partial_{i}\ell_{\theta})\,(\partial_{j}\ell_{\theta}) \right] + \mathbb{E}_{ \theta }\left[  (\partial_{i}\ell_{\theta})\,(\partial_{k}\partial_{j}\ell_{\theta}) \right] + \mathbb{E}_{ \theta }\left[  (\partial_{i}\ell_{\theta})\,(\partial_{j}\ell_{\theta})\,(\partial_{k}\ell_{\theta}) \right] \\[5pt]
>&= \Gamma_{k,i:j}^{(0)} + \Gamma_{k,j:i}^{(0)}
>\end{align*}
>$$

- [[Levi Civita Connection and Riemannian Connection]]

### Exponential Connection and Mixture Connection

![[Exponential Connection and Mixture Connection on Statistical Manifold#^a34e99]]

![[Exponential Connection and Mixture Connection on Statistical Manifold#^fb526f]]

- [[Exponential Connection and Mixture Connection on Statistical Manifold]]


## Explanation


## Invariance to Sufficient Statistics and Uniqueness

>[!important] Theorem
>Denote a finite set as $$\mathcal{X}_{n} := \left\{ 1\,{,}\ldots{,}\,n \right\} $$ and the space of probability measures on $\mathcal{X}_{n}$  as $\mathcal{P}_{n} = \mathcal{P}(\mathcal{X}_{n})$
>- Suppose  $$\{(g_{n}, \nabla_{n})\}_{n=1}^{\infty}$$ is a sequence of *Riemannian metrics* and *affine connections* on $\mathcal{P}_{n}$ for each $n$, respectively.
>- Define $$F: \mathcal{X}_{n} \to \mathcal{X}_{m}$$ as a *surjective mapping*.
>- $$\mathcal{S} \subset \mathcal{P}_{n},\; \mathcal{S}_{F} \subset \mathcal{P}_{m}$$ 
>- The $(g_{n}, \nabla_{n})$ and $(g_{m}, \nabla_{m})$ are induce metrics and connections on $\mathcal{S}$ and $\mathcal{S}_{F}$ by *restriction* and *projection*.
>
>
>Assume that $\{(g_{n}, \nabla_{n})\}_{n=1}^{\infty}$ is **invariant** with respect to **sufficient statistics**; 
>- i.e., for all $n, m,$ and statistical manifold $\mathcal{S} \subset \mathcal{P}_{n},$ and $$F: \mathcal{X}_{n} \to \mathcal{X}_{m}$$ such that $F$ is a **sufficient statistic** for $\mathcal{S}$, the *induced metrics* and *connections* on $\mathcal{S}$ and $S_{F}$ are assumed to be **invariant**.
>
>Then there exist a *positive real number* $c\in \mathbb{R}$ and a real number $\alpha$ such that, 
>- for all $n$, $g_{n}$ **coincides** with the **Fisher metric** on $\mathcal{P}_{n}$ scaled by a factor of $c$, and $\nabla_{n}$ coincides with the **$\alpha$-connection** on $\mathcal{P}_{n}$. $$g_{n} = c\,g, \quad \nabla_{n} = \nabla^{(\alpha)}$$

^ec8eb2

- [[Methods of Information Geometry by Amari]] pp 38
- [[Fisher Metric or Information Metric of Statistical Manifold]]
- [[Fisher Information]]
- [[Sufficient Statistics]]
- [[f-Divergence]]

>[!important]
>In this way, we see that for models on **finite sets**, 
>- the **Fisher metric** (up to a constant factor) 
>- and the **$\alpha$-connections**
>
>are characterized by the **invariance** with respect to **sufficient statistics**.




-----------
##  Recommended Notes and References


- [[Divergence Function on Manifold]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Concepts related to Tangent Space and Tangent Bundle]]

- [[Affine Connection of Basis Frames and Connection Coefficient]]
- [[Connection in Vector Bundle and Covariant Derivative]]

- [[Metric Connection for Riemannian Manifold]]



- [[Methods of Information Geometry by Amari]] pp 32 - 34
- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
