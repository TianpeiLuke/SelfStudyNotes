---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - entropy_functional
topics:
  - information_theory
  - concentration_inequality
name: Phi Entropy Functional
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: $\Phi$-Entropy Functional

>[!important] Definition
>Let $\Phi: [0, \infty) \rightarrow \mathbb{R}$ be a **convex function**.
>
>
>The **$\Phi$-entropy functional** $H_{\Phi}: \Omega \to \mathbb{R}$ is defined by
>$$
>H_{\Phi}\left(g\right) := \int_{\mathcal{X}}\Phi(g) d\mu - \Phi\left( \int_{\mathcal{X}}g\, d\mu \right),
>$$
>where the *domain* $\Omega$ of the functional is defined as
>$$
>\Omega := \left\{ g \in L^1(\mathcal{X}, \mu): g \ge 0 \right\}.
>$$

>[!info]
>We can also call this functional the **$f$-entropy functional** as it induced the **$f$-divergence**.

- [[f-Divergence]]
- [[Convex Function]]

## Explanation

>[!info]
>We can define function $g$ as the **Radon-Nikodym derivative**
>$$
>g := \frac{d\mathcal{P}}{d\mu}
>$$
>where $\mathcal{P} \ll \mu$ is some probability measure. $g$ is the *density function* of $\mathcal{P}$ w.r.t. base measure $\mu$.
>
>If we further assume that
>- $\Phi(x) < +\infty$ for $x >0$;
>- $\Phi(1) = 0$;
>- $\Phi(0)= \lim_{ x \to 0^+ }\Phi(x)$.
>
>Then 
>$$
>\begin{align*}
>H_{\Phi}\left(f\right) &:= \int_{\mathcal{X}} \Phi\left( \frac{dP}{d\mu} \right) d\mu - \Phi\left( \int_{\mathcal{X}}\frac{dP}{d\mu} \, d\mu \right)\\
>&=\int_{\mathcal{X}} \Phi\left( \frac{dP}{d\mu} \right) d\mu
\end{align*}
>$$
>where 
>$$
>\Phi\left( \int_{\mathcal{X}}\frac{dP}{d\mu} \, d\mu \right) = \Phi\left( \int_{\mathcal{X}}d\mathcal{P} \right) = \Phi(1) = 0.
>$$
>
>The right hand side
>$$
>\mathbb{D}_{\Phi}\left( P \left\|\right. Q \right) := \int_{\mathcal{X}} \Phi\left( \frac{dP}{dQ} \right) dQ 
>$$ 
>is called the [[f-Divergence]]. Thus
>$$
>H_{\Phi}\left(f\right) = \mathbb{D}_{\Phi}\left( P \left\|\right. \mu \right). 
>$$

- [[f-Divergence]]

- [[Radon-Nikodym Derivative]]






-----------
##  Recommended Notes and References


- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Entropy Functional]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]