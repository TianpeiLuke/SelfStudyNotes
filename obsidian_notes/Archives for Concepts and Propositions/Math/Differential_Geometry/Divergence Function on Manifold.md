---
tags:
  - concept
  - math/information_theory
  - math/differential_geometry
keywords:
  - divergence_manifold
topics:
  - information_theory
  - differential_geometry
name: Divergence Function on Manifold
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Divergence Function on Manifold

>[!important] Definition
>Given a *differentiable manifold* $\mathcal{M}$ of dimension $n$, a **divergence** on $\mathcal{M}$ is a $C^{2}$-function $\mathbb{D}: \mathcal{M} \times \mathcal{M} \to [0, \infty)$  satisfying:
> 
>- **Non-Negativity**: $$\mathbb{D}\left( p \left\|\right. q \right)  \geq 0$$ for all $p,q\in \mathcal{M}$;
>- **Positivity**: $$\mathbb{D}\left( p \left\|\right. q \right) = 0$$ if and only if $p=q$;
>- At every point $p\in \mathcal{M}$,  $\mathbb{D}\left( p \left\|\right. p + dp \right)$  is a **positive-definite** *quadratic form* for *infinitesimal displacements* $dp$ from $p$. 
>
>The last property means that divergence defines an **inner product** on the *tangent space* $T_{p}\mathcal{M}$ for every $p\in \mathcal{M}$. Since $\mathbb{D}$ is $C^{2}$ on $\mathcal{M}$, this defines a *Riemannian metric* $g$ on $\mathcal{M}$.

- [[Tangent Space Definition and Development]]
- [[Space of Continuous Differentiable Functions]]
- [[Smooth Manifold]]

## Explanation



## Properties

>[!important] Proposition
>Let $\mathcal{M}$ be a *smooth manifold*. 
>
>Define $$\mathbb{D}: \mathcal{M} \times \mathcal{M} \to \mathbb{R}_{+}$$ as a **divergence function** on $\mathcal{M}$.
>- Denote $$\mathbb{D}(p_{\theta}\;\|\;q_{\eta})$$ where $p$ and $q$ have parameters $\theta, \eta\in \Theta$, respectively.
>- Consider **restricting $\mathbb{D}$ to diagonal** $\{ (p,q) \in \mathcal{M}\times \mathcal{M}: p= q \}$
>
>Then 
>- the **1st-order partial derivative** of *divergence* with respect to either points **vanishes** when **restricting** to **diagonal** $$\frac{\partial }{ \partial \theta^{i}}\,\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q} =  \frac{\partial }{ \partial \eta^{i}}\,\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q} = 0$$
>- the **2nd-order partial derivative** of *divergence* with respect to either points is **positive semidefinite** when *restricting to diagonal*, i.e. $$I^{(\mathbb{D})} = [g_{i,j}^{\mathbb{D}}] \succeq 0$$ where 
>$$
>\begin{align*}
>g_{i,j}^{\mathbb{D}}&:= \frac{\partial^2 }{ \partial \theta^{i}\partial \theta^{j}}\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q}\\[8pt] 
>&= \frac{\partial^2 }{ \partial \eta^{i}\partial \eta^{j}}\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q}\\[8pt] 
>&= -\frac{\partial }{ \partial \theta^{i}}\frac{\partial }{\partial \eta^{j}}\,\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q} 
>\end{align*}
>$$
>- The **second-order approximation** of *divergence* is given by $$\mathbb{D}(p_{\theta}\;\|\;q_{\theta}) = \frac{1}{2}g_{i,j}^{\mathbb{D}}(q)\,d\theta^{i}\,d\theta^{j} + o(\lVert \Delta \theta \rVert^2 )$$ where $d\theta^{i} = \theta^{i}(p) - \theta^{i}(q)$
>
>Thus, given divergence function $\mathbb{D}$, there exists a **unique Riemannian metric** $g^{\mathbb{D}}$ so that $$\left\langle  \partial_{i}\,,\,\partial_{j} \right\rangle^{\mathbb{D}} = g_{i,j}^{\mathbb{D}}$$ or $$\left\langle  X\,,\, Y \right\rangle^{\mathbb{D}} := - \mathbb{D}(X\;\|\;Y)$$
>where $$\mathbb{D}(\partial_{i}\;\|\;\partial_{j}) := \frac{\partial }{ \partial \theta^{i}}\frac{\partial }{\partial \eta^{j}}\,\mathbb{D}(\cdot\;\|\;\cdot)\Big|_{p = q}.$$

- [[Riemannian Metric and Riemannian Manifold]]



-----------
##  Recommended Notes and References


- [[Tangent Space Definition and Development]]

- [[Fisher Information]]

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Concepts and Theorems for Riemannian Manifold]]
- [[Methods of Information Geometry by Amari]] pp 53 - 56