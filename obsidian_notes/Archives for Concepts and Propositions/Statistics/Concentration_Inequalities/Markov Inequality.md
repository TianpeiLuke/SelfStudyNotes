---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - markov_inequality
topics:
  - statistics
name: Markov's Inequality
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Markov's Inequality

>[!important] Markov's Inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X \in L^1(\Omega, \mathcal{P})$ is an *non-negative integrable random variable*, i.e. $X \ge 0, a.s.$. Then for all $t > 0$,
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] &\le  \frac{\mathbb{E}\left[X \right]}{t}
> \end{align*}
> $$

- [[Expectation of Random Variable]]
- [[Absolutely Convergent Integration]]

>[!proof]
>Note that since $X \ge 0, a.s.$, we have
>
> $$
> \begin{align*}
> X \;\mathbb{1}(X \ge t) & \ge t \;\mathbb{1}(X \ge t)\\
> \implies \mathbb{E}\left[ X \;\mathbb{1}(X \ge t) \right] := \int_{\Omega} X \mathbb{1}(X \ge t) d\mathcal{P} &\ge \int_{\Omega} t \mathbb{1}(X \ge t) d\mathcal{P} := t \mathcal{P}\left[X \ge t\right] \\
> \implies \mathcal{P}\left[X \ge t\right] &\le \frac{\mathbb{E}\left[ X \;\mathbb{1}(X \ge t) \right]}{t} \le \frac{\mathbb{E}\left[ X \right]}{t}
> \end{align*}
> $$
> The last step holds since $\mathbb{1}\{A\} \le 1$. \qed

## Generalization

- This inequality can be extended to any *nondecreasing and nonnegative* function $\phi$

>[!important]
>Let $\phi: I \subseteq \mathbb{R} \to \mathbb{R}$ be any *nondecreasing and nonnegative* function, and if $X$ denotes a random variable taking values in $I$,  then *Markov’s inequality* implies that for every $t \in I$ with $\phi(t) > 0,$
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] \le \mathcal{P}\left[\phi(X) \ge \phi(t)\right] &\le  \frac{\mathbb{E}\left[\phi(X)  \right]}{\phi(t)}.
> \end{align*}
> $$





-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Concentration Inequalities by Boucheron]]