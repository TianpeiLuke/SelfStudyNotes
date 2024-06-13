---
tags:
  - concept
  - math/probability
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - doob_maximal_inequality
topics:
  - concentration_inequality
  - stochastic_process
name: Doob Maximal Inequality
date of note: 2024-05-15
---

## Concept Definitions

>[!important]
>**Name**: Doob Maximal Inequality

>[!important] Doob's Maximal Inequality
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **sub-martingale**. 
>
>Then for any $t >0$, 
>$$
> \begin{align}
> \mathcal{P}\left\{\max_{k \le n}X_k \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_n \mathbb{1}\left\{\max_{k \le n}X_k \ge t \right\} \right] 
> \end{align}
>$$ 

- [[Sub-Martingale]]
- [[Stopping Time of Filtration]]
- [[Doob Optional Sampling Theorem]]

## Variation with Bounded Condition

>[!important] Doob's Maximal Inequality (sub-martingale with bounded condition)
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **sub-martingale** and 
>$$
>X_{n} \ge 0, \;\; \forall n \quad \text{a.s.}
>$$
>
>Then for any $t >0$,
>$$
> \begin{align}
> \mathcal{P}\left\{\max_{k\le n}X_k \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_n \right]. 
> \end{align}
>$$ 



>[!important] Doob's Maximal Inequality (super-martingale with bounded condition)
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **super-martingale** and 
>$$
>X_{n} \ge 0, \;\; \forall n \quad \text{a.s.}
>$$
>
>Then for any $t >0$,
>$$
> \begin{align}
> \mathcal{P}\left\{\sup_{k\in \mathbb{N}}X_k \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_0 \right]. 
> \end{align}
>$$ 


>[!important] Doob's Maximal Inequality (martingale with $p$-norm)
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **martingale** and  $1 < p < \infty.$
>
>Then for any $t >0$,
>$$
> \begin{align}
> \mathcal{P}\left\{\sup_{k\le n} |\,X_k\,|^p \ge t  \right\} \le \left(\frac{p}{p - 1}\right)^p\, \mathbb{E}_{}\left[ |X_n|^{p} \right]. 
> \end{align}
>$$ 



## Explanation

>[!info]
>Doob's Maximal inequality has similar form as the [[Markov Inequality]], 
>$$
> \begin{align}
> \mathcal{P}\left\{X_n \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_0 \right]. 
> \end{align}
>$$ 

>[!info]
>Doob's Maximal inequality is effectively applies to the stopping time $\tau$, for $X_{\tau}$: 
>$$
>\mathcal{P}\left\{X_{\tau} \ge t  \right\} 
>$$

>[!important]
>Doob's Maximal Inequality is a **strict improvement** of the Markov Inequality as we replace $X_{n}$ with $\sup_{n\in \mathbb{N}}X_{n}$ with no cost on the upper bound.


>[!info]
>Doob's Maximal inequality for the **maximum variation of empirical process**. [[Empirical Process and Empirical Measure]]






-----------
##  Recommended Notes and References


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]

- [[Bandit Algorithms by Lattimore]]
- [[Probability and Measure by Billingsley]]
