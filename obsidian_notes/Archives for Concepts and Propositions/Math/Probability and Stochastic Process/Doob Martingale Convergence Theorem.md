---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - martingale_convergence_theorem
topics:
  - stochastic_process
  - probability
name: Doob's Martingale Convergence Theorem
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**: Doob's Martingale Convergence Theorem

>[!important] Doob's Martingale Convergence Theorem
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **super-martingale** and suppose further that
>$$
> \begin{align*}
> \sup_{n}\mathbb{E}\left[ |X_{n}| \right] < \infty.
> \end{align*}
>$$  
>Then there exists an integrable random variable $X$ such that 
>$$
> \begin{align*}
> \lim\limits_{n \to \infty}X_n = X \quad \text{a.s.}
> \end{align*}
>$$ 

- [[Super-Martingale]]
- [[Doob Optional Sampling Theorem]]
- [[Doob Maximal Inequality]]
- [[Pointwise Almost Everywhere Convergence]]

## Explanation

>[!info]
>Intuitively, the **super-martingale** is a **non-increasing process**

- [[Predictable and Increasing Process]]

>[!important]
>This theorem is a stochastic variant of the **monotone convergence theorem**.

- [[Monotone Convergence Theorem]]

>[!info]
>Similar convergence results hold for **sub-martingale**, which is a *increasing process*.
>
>As a result, this theorem holds for **martingale.**


>[!important]
>This theorem is a generalization of the **strong law of large numbers (SLLN)** from **independent samples** to **martingales**.

- [[Kolmogorov Strong Law of Large Numbers]]





-----------
##  Recommended Notes and References


- [[Bandit Algorithms by Lattimore]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]
- [[Introduction to Stochastic Calculus by Klebaner]]
- Wikipedia [martingale_convergence_theorems](https://en.wikipedia.org/wiki/Doob%27s_martingale_convergence_theorems)