---
tags:
  - concept
  - math/convex_analysis
  - math/functional_analysis
keywords:
  - perspective_function
topics:
  - convex_analysis
  - functional_analysis
name: Perspective of a Function
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Perspective of a Function

>[!important] Definition
>Let $\mathcal{H}$ be a *real Hilbert space*, and let $\varphi: \mathcal{H} \to (-\infty,+\infty]$ be a **convex function**.
>
>The **perspective function** of $\varphi$ is 
>$$
> \xi := \mathscr{P}_{\varphi}: \mathbb{R} \times \mathcal{H} \to (-\infty,+\infty]
>$$
>defined as
>$$
> (\eta, y) \mapsto \left\{ 
> \begin{array}{cc}
> \eta\,\varphi\left( \dfrac{y}{\eta} \right), & \eta >0\\ 
> +\infty, & \text{otherwise.}
>\end{array}
> \right.
>$$

^4c8078


## Explanation



## Convex Function

>[!important] Proposition
>Let $\mathcal{H}$ be a *real Hilbert space*, and let $\varphi: \mathcal{H} \to (-\infty,+\infty]$ be a real-valued function on $\mathcal{H}$. Denote $\mathscr{P}_{\varphi}: \mathbb{R} \times \mathcal{H} \to (-\infty,+\infty]$ as the *perspective function* of $\varphi$.
>
>Then the **perspective function** $\mathscr{P}_{\varphi}$ of $\varphi$ is **convex** *if and only if* $\varphi$ is **convex**.

^7f2372

## $f$-Divergence

![[f-Divergence#^e7fa76]]


>[!important]
>Define $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function satisfying the following conditions:
>- $f(x) < +\infty$ for $x >0$;
>- $f(1) = 0$;
>- $f(0)= \lim_{ x \to 0^+ }f(x)$.
>
>Let $p$ and $q$ be the **probability density function (i.e. Radon-Nikodym derivative)** of $P$ and $Q$ with respect to Lebesgue measure, i.e.
>$$
>dP = p(x)\,dx, \quad dQ = q(x)\,dx.
>$$
>
>Assume $\mathcal{H} = \mathbb{R}$. Then the *perspective function* of $f$ 
>$$
>\begin{align*}
> \mathscr{P}_{f}(q(x), p(x)) := q(x)\,f\left( \frac{p(x)}{q(x)} \right)
>\end{align*}
>$$
>and the **integral of perspective function** of $f$
>$$
>\begin{align*}
> \int_{\mathcal{X}}\mathscr{P}_{f}(q(x), p(x))\,dx &:= \int_{\mathcal{X}}f\left( \frac{p(x)}{q(x)} \right)q(x)\,dx\\[10pt]
> &=  \mathbb{D}_{f}\left( P \left\|\right. Q \right)
>\end{align*}
>$$

- [[f-Divergence]]
- [[Radon-Nikodym Derivative]]

## Examples





-----------
##  Recommended Notes and References

- [[Convex Function]]
- [[Operations that Preserve Convexity]]


- [[Convex Optimization by Boyd]]
- Combettes, P. L. (2017). _Perspective Functions: Properties, Constructions, and Examples_ (arXiv:1610.01552). arXiv. [https://doi.org/10.48550/arXiv.1610.01552](https://doi.org/10.48550/arXiv.1610.01552)