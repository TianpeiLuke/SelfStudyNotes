---
tags:
  - concept
  - math/real_analysis
keywords:
  - integration_by_parts
  - weak_derivative
  - strong_derivative
topics:
  - real_analysis
name: Integration by Parts
date of note: 2024-06-10
---

## Concept Definition

>[!important]
>**Name**: Integration by Parts

### Riemann Integral

>[!important] Theorem
>Suppose $F$ and $G$ are **differentiable** functions on $[a, b]$, $F' = f \in \mathcal{R}$, and $G' = g \in \mathcal{R}$. 
>
>Then
>$$
>\begin{align*}
>\int_{a}^{b}\,F(x)\,g(x)\,dx = - \int_{a}^{b}\,G(x)\,f(x)\,dx + F(b)\,G(b) - F(a)\,G(a). 
>\end{align*}
>$$
>or
>$$
>\begin{align*}
>\int_{a}^{b}\,F(x)\,G'(x)\,dx = - \int_{a}^{b}\,G(x)\,F'(x)\,dx + F(b)\,G(b) - F(a)\,G(a). 
>\end{align*}
>$$

- [[Riemann Integration]]

### Riemann Integral

>[!important] Proposition
>Suppose $F$ is **monotonically increasing** on $[a,b]$, and $g$ is **continuous**, and $g(x) = G'(x)$ for $x\in [a,b]$. 
>$$
>\int_{a}^{b} F(x)\,g(x)\,dx = - \int_{a}^{b} G(x)\,dF(x) + F(b)G(b) - F(a)G(a)
>$$

- [[Riemann–Stieltjes Integration]]

### Lebesgue Integral

>[!important] Proposition
>Let $F: [a,b] \to \mathbb{R}$ be an **absolutely continuous** function and $\phi: [a,b] \to \mathbb{R}$ be a **continuous differentiable** function *supported* in a **compact subset** of $(a,b)$
>
>Then 
>$$
>\begin{align*}
>\int_{[a,b]}F'\,\phi\,dx = - \int_{[a,b]}F\,\phi'\,dx
>\end{align*}
>$$

- [[Absolutely Convergent Integration]]
- [[Absolutely Continuous Function]]
- [[Second Fundamental Theorem of Calculus Absolutely Continuous]]

>[!info]
>Since $F$ is absolutely continuous, $F$ is of bounded variation, thus [[Bounded Variation Differentiation Theorem]], $F$ is almost *everwhere differentiable*.


## Explanation

>[!important]
>The property of **integration by parts** can be generalized as the definition of *derivatives* when $F$ is *not necessarily differentiable*. 
>
>Thus derivative of $F$, $DF$, defined by 
>$$
>\begin{align*}
>\int_{[a,b]}(D\,F)\,\phi\,dx = - \int_{[a,b]}F\,\phi'\,dx
>\end{align*}
>$$
>is called the **weak derivative** where $\phi$ is called a **test function**.
>
>For $F$ being **absolutely continuous**, the *strong* and *weak derivative* is the **equivalent**.

- [[Weak Derivative via Tempered Distribution]]





-----------
##  Recommended Notes and References


- [[Riemann Integration]]
- [[Riemann–Stieltjes Integration]]
- [[Lebesgue-Stieltjes Integration]]


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]

- Rudin, W. (1964). _Principles of mathematical analysis_ (Vol. 3). New York: McGraw-hill.
- Abbott, S. (2015). _Understanding analysis_. Springer.