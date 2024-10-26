---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - weak_derivative
  - derivative_tempered_distribution
topics:
  - functional_analysis
  - topology
name: Weak Derivative and Derivative in Tempered Distribution
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Weak Derivative and Derivative in Tempered Distribution


>[!important] Definition
>Let $T \in \mathscr{S}'(\mathbb{R}^n)$ be a *tempered distribution*, $\alpha\in I_{+}^n$. 
>
>The **weak derivative**, $D^{\alpha}T$, or  **the derivative in the sense of distributions** is defined by
>$$
>\begin{align*}
>(D^\alpha T)(f) := (-1)^{|\alpha|}\,T\left(D^\alpha f\right).
>\end{align*}
>$$
>The function $T\in \mathscr{S}'(\mathbb{R}^n)$ is called a **test function**.
>
>In symbolic notation
>$$
>\int_{\mathbb{R}^n} \left(D^{\alpha}T(x)\right)\,f(x)\,dx = (-1)^{|\alpha|}\,\int_{\mathbb{R}^n} T(x)\,\left(\frac{ \partial^{|\beta|} }{ \partial x_{1}^{\beta_{1}} \, \ldots \, \partial x_{n}^{\beta_{n}}} f \right)(x)\,dx.
>$$

- [[Space of Tempered Distributions]]
- [[Locally Convex Space]]
- [[Norm and Normed Space]]
- [[Semi-Norm that Separating Points]]

>[!important] Definition
>Suppose $u, v\in L_{loc}^1(\Omega)$ and $\alpha$ is a multi-index.
>
>We say $v \in L_{loc}^1(\Omega)$ is the **$\alpha$-th weak derivative** of $u$ if
>$$
>\int\, u\, D^{\alpha}\varphi \; dx= (-1)^{|\alpha|}\,\int\, v\, \varphi \; dx,
>$$
>for all **test functions** $\varphi \in \mathcal{C}^{\infty}(\Omega).$ 
>
>It is written as $$D^{\alpha}u = v,$$ in **weak (distribution sense)**.

^13abe5

- [[Locally Integrable Function]]
- [[Space of Tempered Distributions]]




## Explanation

>[!important]
> A **weak derivative** is a **generalization** of the concept of the *derivative* of a function for functions **not assumed differentiable**, but **only integrable**.
> $$
>v= D^{\alpha}u \implies \int\, u\, D^{\alpha}\varphi \; dx= (-1)^{|\alpha|}\,\int\, v\, \varphi \; dx.
>$$


>[!important]
>The definition of *weak derivative* generalize the idea of **integration by parts**.

- [[Integration by Parts]]

>[!important]
>For a function $u \in L^1([a,b])$, we say $v\in L^1([a, b])$ is a **weak derivative of** $u$ if
>$$
>\int_{a}^{b} u(t)\,\varphi'(t)\,dt = - \int_{a}^{b} v(t)\,\varphi(t)\,dt, 
>$$
>for all $\varphi \in \mathcal{C}^{\infty}([a, b])$,  $\varphi(a)= \varphi(b) = 0.$ The function $\varphi: [a,b] \to \mathbb{R}$ is a **test function**.

- [[Sobolev Space]]



-----------
##  Recommended Notes and References

- [[Smooth Map between Euclidean Spaces]]
- [[Fréchet Space]]

- [[Space of Tempered Distributions]]
- [[Space of Functions of Rapid Decrease and Schwartz Class]]

- [[Locally Convex Space]]
- [[Norm and Normed Space]]
- [[Semi-Norm that Separating Points]]
- [[Vector Space over a Field]]



- [[Functional Analysis by Reed]]
- Wikipedia [Weak derivative](https://en.wikipedia.org/wiki/Weak_derivative)