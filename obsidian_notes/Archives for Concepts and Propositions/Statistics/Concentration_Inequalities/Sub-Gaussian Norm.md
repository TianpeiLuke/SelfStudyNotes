---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - sub-gaussian_norm
topics:
  - statistics
name: Sub-Gaussian Norm
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Sub-Gaussian Norm

- [[Sub-Gaussian Random Variable]]

>[!important] Definition
>The **sub-gaussian norm** of $X$, denoted $\lVert X \rVert_{\psi_2}$, is defined to be the **smallest** $K_4$ that satisfies 
>$$
> \begin{align*}
> \mathbb{E}_{}\left[ \exp(X^2 / K_4^2) \right]  \le 2.
> \end{align*}
>$$  
>In other words, we define
>$$
>\begin{align}
> \lVert X \rVert_{\psi_2} := \inf\left\{t > 0: \mathbb{E}_{}\left[ \exp(X^2 / t^2) \right] \le 2 \right\}. 
>\end{align}
>$$

^67d04f



## Explanation

>[!info]
>Consider the function
>$$
>\psi_{2}(x) := \exp(x^2) - 1.
>$$
>We can show that $\psi_{2}$ is an **Orlicz function**. The resulting **Orlicz norm** is the sub-Gaussian norm. 
>$$
>\lVert X \rVert_{\psi_{2}} := \inf\left\{t>0: \mathbb{E}_{}\left[ \psi_{2} \left(\frac{\lvert X \rvert }{t} \right)\right]  \le 1 \right\}. 
>$$

- [[Orlicz Space]]


## Examples



>[!example]
>Any **bounded random variable** $X$ is **sub-gaussian** with
>$$
> \begin{align*}
> \lVert X \rVert_{\psi_2}\le C \lVert X \rVert_{\infty}
> \end{align*}
>$$
> where $C = 1/\sqrt{\log 2}$.





-----------
##  Recommended Notes and References

- [[Chernoff Bound for Gaussian distribution]]
- [[Cramér–Chernoff Method]]


- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Concentration Inequalities by Boucheron]]