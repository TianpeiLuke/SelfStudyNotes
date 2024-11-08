---
tags:
  - concept
  - math/information_theory
keywords:
  - f_divergence
  - variational_inference
topics:
  - information_theory
name: Variational Formula for f-Divergence
date of note: 2024-05-07
---

## Theorem

>[!important]
>**Name**: Variational Formula for $f$-Divergence

![[f-Divergence#^e7fa76]]



>[!important] Theorem
>Let $P$, $Q$ be two *probability measures* on $(\Omega, \mathscr{F})$, and $P$ be *absolutely continuous* with respect to $Q$, $f$ be a *convex function* on $[0,\infty)$ that satisfies the conditions above.
>
>Denote $f^{*}$ as *the convex conjugate* of $f$, and $\text{effdom}(f^{*})$ is the *effective domain* 
>$$
>\text{effdom}(f^{*}) := \{x^{*} \in \mathbb{R}: f^{*}(x^{*}) < + \infty \}.
>$$
>
>Then the following equation holds
>$$
>\begin{align*}
> \mathbb{D}_{f}\left( P \left\|\right. Q \right) &= \sup\left\{\; \mathbb{E}_{P}\left[ g \right] - \mathbb{E}_{Q}\left[ f^{*} \circ g \right]: \forall g: \text{ bounded, measurable on }\Omega \;\right\}  &\\[8pt]
> &= \sup_{g}\left\{\; \int_{\Omega}\,g\,dP - \int_{\Omega}\,f^{*}(g)\,dQ \; \right\} &\\[8pt]
> &:=  \sup_{g}\left\{\; \mathbb{E}_{P}\left[ g(X) \right] - \mathbb{E}_{Q}\left[ f^{*}(g(X)) \right] \; \right\} & (1)
>\end{align*}
>$$
>or
>$$
>\begin{align*}
>\sup_{P\in \mathcal{M}(\Omega; Q)}\left\{ \int_{\Omega}\,g\,dP -  \mathbb{D}_{f}\left( P \left\|\right. Q \right)\right\} &= \int_{\Omega}\,f^{*} \circ g\;dQ & (2)
>\end{align*}
>$$
>where 
>- The supremum in $(1)$ is taken for all *bounded real-valued measurable function*  $$g: \Omega \to \text{effdom}(f^{*}) \subset \mathbb{R} \implies \; \sup_{\Omega}\lvert g(x) \rvert < \infty $$
>- $\mathcal{M}(\Omega; Q)$ in $(2)$ is the *space of bounded signed finite measures* on $\Omega$ that are absolutely continuous with respect to $Q$.  $$\mathcal{M}(\Omega; Q) := \left\{ P: \mathscr{F} \to (0, +\infty):\; P \ll Q, \quad \lvert P \rvert < \infty  \right\} $$
>
>This formula is called **the variational representation** of $f$-divergence.

^9e3cf2


- [[f-Divergence]]
- [[Convex Function]]
- [[Convex Conjugate Function]]
- [[Proper Convex Function]]
- [[Space of Bounded Signed Measures]]
- [[Absolute Continuity for Measures]]

### Proof

![[Convex Conjugate Function#^2763c0]]

>[!info] Proof
>Note that for closed proper convex function $f$, 
>- $$f^{*}(x^{*}) := \sup_{x\in \mathbb{R}}\left\{ x^{*}\,x - f(x)\right\} $$
>- $f = f^{**}$ as 
>$$
>f(x) = \sup_{x^{*}\in \mathbb{R}}\left\{ x\,x^{*} - f^{*}(x^{*})\right\} 
>$$
>
>Also by **Fenchel's duality theorem**
>$$
>\inf_{x: Ax = b}\left\{ f(x) \right\}  = \sup_{y}\;\left\{ \left\langle  b\,,\,y    \right\rangle - f^{*}\left(A^{T}y\right) \right\} 
>$$
>
>Note that for fixed $Q$, $$P \to  \mathbb{D}_{f}\left( P \left\|\right. Q \right) $$ is *convex.*
>


- [[Fenchel Inequality]]
- [[Fenchel Duality Theorem]]


## Explanation






## Compare with Variational Formula for Wasserstein Distance

![[Variational Representation of Wasserstein Distance#^7ba1e7]]

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Variational Formulation of Optimal Transport]]
- [[Optimal Transport in Space of Measures]]

>[!important]
>- **Wasserstein distance** $$\mathcal{W}_{1}(\alpha, \beta) = \sup\left\{ \int_{\mathcal{X}}\phi\;d\alpha -  \int_{\mathcal{X}}\phi\;d\beta:  \;\forall \phi \in \mathcal{C}(\mathcal{X}) \text{ with } \text{Lip}(\phi) \le 1 \right\}$$
>- **$f$-divergence** $$\mathbb{D}_{f}\left( \alpha \left\|\right. \beta \right) = \sup\left\{ \int_{\mathcal{X}}\,\phi\;d\alpha - \int_{\mathcal{X}}\,f^{*}(\phi)\,d\beta:\; \forall \phi \in \mathcal{B}(\mathcal{X}) \text{ and measureable}  \right\} $$





-----------
##  Recommended Notes and References


- [[Variational Formula for Entropy Functional]]
- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]

- [[Absolute Continuity for Measures]]


- [[wanFDivergenceVariationalInference2020]]
- Broniatowski, M., & Keziou, A. (2006). Minimization of φ-divergences on sets of signed measures. _Studia Scientiarum Mathematicarum Hungarica_, _43_(4), 403-442.
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 888 - 889
- [[Elements of Information Theory by Cover]]
- Wikipedia [F-divergence](https://en.wikipedia.org/wiki/F-divergence)

