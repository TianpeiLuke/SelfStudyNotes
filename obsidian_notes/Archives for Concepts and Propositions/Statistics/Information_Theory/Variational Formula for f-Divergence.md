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

>[!info] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>Define $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function satisfying the following conditions:
>- $f(x) < +\infty$ for $x >0$;
>- $f(1) = 0$;
>- $f(0)= \lim_{ x \to 0^+ }f(x)$.
>
>Then **$f$-Divergence** *from* $Q$ to $P$ is defined as
> $$
> \begin{align*}
> \mathbb{D}_{f}\left( P \left\|\right. Q \right) &:= \int_{\Omega} f\left( \frac{dP}{dQ} \right) dQ 
> \end{align*}
> $$
> where $\frac{dP}{dQ}$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.
> 
> We call $f$ the **generator** of $\mathbb{D}_{f}\left( \cdot \left\|\right. \cdot \right).$

- [[f-Divergence]]

>[!important] Theorem
>Let $P$, $Q$ be two *probability measures* on $(\Omega, \mathscr{F})$, and $P$ be *absolutely continuous* with respect to $Q$, $f$ be a *convex function* that satisfies the conditions above.
>
>Denote $f^{*}$ as *the convex conjugate* of $f$, and $\text{effdom}(f^{*})$ is the *effective domain* 
>$$
>\text{effdom}(f^{*}) := \{x^{*}: f^{*}(x^{*}) < + \infty \}.
>$$
>
>Then the following equation holds
>$$
>- \mathbb{D}_{f}\left( P \left\|\right. Q \right) = \sup\{ \mathbb{E}_{P}\left[ g \right] - \mathbb{E}_{Q}\left[ \exp\left(f^{*} \circ g\right) \right]: \forall g: \Omega \to  \text{effdom}(f^{*}) \}
>$$
>
>This formula is called **the variational representation** of $f$-divergence.



## Explanation



## Properties



-----------
##  Recommended Notes and References

- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Divergence on Manifold]]

- [[wanFDivergenceVariationalInference2020]]
- [[Elements of Information Theory by Cover]]
- Wikipedia [F-divergence](https://en.wikipedia.org/wiki/F-divergence)

