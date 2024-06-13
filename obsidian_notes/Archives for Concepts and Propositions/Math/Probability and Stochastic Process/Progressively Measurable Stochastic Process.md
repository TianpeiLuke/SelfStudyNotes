---
tags:
  - concept
  - math/stochastic_process
keywords:
  - progressive_measureable_stochastic_process
topics:
  - stochastic_process
name: Progressively Measurable Stochastic Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Progressively Measurable Stochastic Process

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be probability space and $(\mathbb{R}, \mathcal{B}[\mathbb{R}], \mu)$ be a *Borel measure space*. Define $T \subset \mathbb{R}$. Also let $\mathscr{F}_{n} \subseteq \mathscr{F}_{n+1} \,{\subseteq}\ldots{\subseteq}\,\mathscr{F}$ be a *filtration*.
>
>A *stochastic process* $(X_{t}, t\in T)$ is called **progressively measurable** if 
>- $X: \Omega \times T \to \mathbb{R}$ is $\mathscr{F} \times \mathcal{B}[\mathbb{R}]$ *measureable*.
>- $X_{t}$ is $\mathscr{F}_{t}$-*adapted*. 
>- and
>$$
>\mathbb{E}_{\mathcal{P}}\left[ \int_{T} |X_{t}| dt \right] = \int_{\Omega}\;\int_{T} |X(\omega, t))| dt\; d\mathcal{P}(\omega)  < \infty.
>$$
>
>Denote the **space** of all **real-valued progressively measurable stochastic process** as $$\mathbb{L}^1(T).$$

- [[Measurable Function]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Filtration]]

- [[Absolutely Convergent Integration]]
- [[Expectation of Random Variable]]
- [[Stochastic Process]]
- [[Lp Space]]


>[!important] Definition
>Denote $$\mathbb{L}^2(T)$$ as the **space** of all **real-valued progressively measurable stochastic process** such that 
>- $X: \Omega \times T \to \mathbb{R}$ is $\mathscr{F} \times \mathcal{B}[\mathbb{R}]$ *measureable*.
>- $X_{t}$ is $\mathscr{F}_{t}$-*adapted*. 
>- and
>$$
>\mathbb{E}_{\mathcal{P}}\left[ \int_{T} X_{t}^2 dt \right] = \int_{\Omega}\;\int_{T} (X(\omega, t)))^2 dt\; d\mathcal{P}(\omega)  < \infty.
>$$
>
>

>[!info]
>$$\mathbb{L}^2(0,T)$$ is an **inner product space** with inner product 
>$$
>\left\langle X , Y \right\rangle_{\mathbb{L}^2(0,T)} :=  \mathbb{E}\left[  \int_{0}^{T} X_{t}\,Y_{t}\;dW  \right] 
>$$

- [[Inner Product Space]]
- [[Hilbert Space]]
- [[Itô Isometry]]


>[!important] Definition
>Denote $$\mathbb{M}^2(T)$$ as the **space** of all **real-valued progressively measurable stochastic process** such that 
>- $X: \Omega \times T \to \mathbb{R}$ is $\mathscr{F} \times \mathcal{B}[\mathbb{R}]$ *measureable*.
>- $X_{t}$ is $\mathscr{F}_{t}$-*adapted*. 
>- and
>$$
>\int_{T} X_{t}^2 dt  = \int_{T} (X(\omega, t))^2 dt < \infty, \quad \text{ a.s.}
>$$
>
>


## Explanation

>[!important]
>The idea is that the stochastic process $((X_{t}, \mathscr{F}_{t}), t\in T)$ 
> - is **adapted (nonanticipating)** and, in addition, 
> - is *appropriately* **jointly measurable** in the variables $t$ and $\omega$ **together**.


## Approximation via Step Process

>[!important] Theorem
>If $X \in \mathbb{L}^2(T)$, then there exists a **sequence of bounded step processes** $$X^n \in \mathbb{L}^2(T)$$ such that 
>$$
>\begin{align*}
>\mathbb{E}_{\mathcal{P}}\left[\int_{T}\left(X^n - X\right)^2 dt \right] := \int_{\Omega}\;\int_{T}\left(X^n(\omega, t) - X(\omega, t)\right)^2 dt\; d\mathcal{P}(\omega)\to 0
>\end{align*}
>$$
>as $n\to \infty$.

^7e5649

>[!info]
>- If $X(\cdot, t)$ is continuous, we can use [[Stone-Weierstrass Theorem]] to define polynomial function to approximate the continuous sample path.
>- If not, define $$X^n(t) := \int_{0}^{t}n\,\exp(n(s -t))\,X(s)\,ds$$

- [[Step Process]]



-----------
##  Recommended Notes and References

- [[Absolutely Convergent Integration]]
- [[Expectation of Random Variable]]
- [[Stochastic Process]]
- [[Lp Space]]

- [[Itô Stochastic Integration]]

- [[Introduction to Stochastic Differential Equations by Evans]]
- Wikipedia [Progressively measurable process](https://en.wikipedia.org/wiki/Progressively_measurable_process)