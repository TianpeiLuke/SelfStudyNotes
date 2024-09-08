---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - chebyshev_inequality
topics:
  - statistics
name: Chebyshev’s Inequality
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Chebyshev's Inequality

>[!info]
>Let $\phi: I \subseteq \mathbb{R} \to \mathbb{R}$ be any *nondecreasing and nonnegative* function, and if $X$ denotes a random variable taking values in $I$,  then *Markov’s inequality* implies that for every $t \in I$ with $\phi(t) > 0,$
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] \le \mathcal{P}\left[\phi(X) \ge \phi(t)\right] &\le  \frac{\mathbb{E}\left[\phi(X)  \right]}{\phi(t)}.
> \end{align*}
> $$

>[!info]
>Set $\phi(x) = x^2$, for $I = (0, +\infty)$, we obtain the Chebyshev's inequality

>[!important] Chebyshev's Inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X \in L^2(\Omega, \mathcal{P})$ is a *random variable* with *finite variance*. Then for all $t > 0$,
> $$
> \begin{align*}
> \mathcal{P}\left[ \lVert X - \mathbb{E}\left[X\right] \rVert \ge t\right] &\le  \frac{\text{Var}\left(X \right)}{t^2}
> \end{align*}
> $$

^1f4106

## Explanation



## Generalization

- This inequality can further be extended to *any $L^p$ norm*, where $\phi(x) = x^p$, $p > 0$.

>[!important]
>If $X \in L^p(\Omega, \mathcal{P})$, where $p >0$, then for all $t > 0$,
 >$$
> \begin{align*}
> \mathcal{P}\left[ \lVert X - \mathbb{E}\left[X\right] \rVert \ge t\right] &\le  \frac{\mathbb{E}\left[ \lVert X - \mathbb{E}\left[X\right] \rVert^p  \right]}{t^p}
> \end{align*}
> $$




-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Markov Inequality]]
- [[Concentration Inequalities by Boucheron]]