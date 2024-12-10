---
tags:
  - concept
  - math/probability
keywords:
  - weak_law_large_number
topics:
  - probability
name: Weak Law of Large Numbers
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Weak Law of Large Numbers (WLLN)

>[!important] General Weak Law of Large Numbers (WLLN)
>Suppose $\left\{ X_{n},  n \ge 1 \right\}$ are **independent** random variables and define
>$$
>S_{n} = \sum_{j=1}^{n}X_{j}.
>$$
>If 
>- $$\sum_{j=1}^n\mathcal{P}\left[ |X_{j}| > n \right] \to 0,$$
>- $$\frac{1}{n^2}\sum_{j=1}^{n} \mathbb{E}_{}\left[ X_{j}^2\; \mathbb{1}\left\{ |X_{j}| \le n \right\}  \right] \to 0,$$
>
>then if we define
>$$
>a_{n} = \sum_{j=1}^{n} \mathbb{E}\left[  X_{j}\; \mathbb{1}\left\{ |X_{j}| \le n \right\} \right],
>$$
>we get 
>$$
>\frac{S_{n} - a_{n}}{n} \stackrel{\mathcal{P}}{\rightarrow} 0.
>$$


## Special Cases

>[!important] Weak Law of Large Numbers with variances (WLLN)
>Suppose $\left\{ X_{n},  n \ge 1 \right\}$ are **independent identically distributed (i.i.d.)** random variables with 
>- $$ \mathbb{E}\left[ X_{n} \right] = \mu,\;$$ 
>- $$ \mathbb{E}\left[ X_{n}^2 \right] < +\infty. $$
>
>Then as $n\to \infty$, 
>$$
>\frac{1}{n} S_{n} \stackrel{\mathcal{P}}{\rightarrow} \mu.
>$$

>[!important] Weak Law of Large Numbers with first moment hypothesis (WLLN)
>Suppose $\left\{ X_{n},  n \ge 1 \right\}$ are **independent identically distributed (i.i.d.)** random variables with 
>- $$ \mathbb{E}\left[ | X_{n} | \right] < + \infty,\;$$ 
>- $$ \mathbb{E}\left[ X_{n} \right] = \mu. $$
>
>Then as $n\to \infty$, 
>$$
>\frac{1}{n} S_{n} \stackrel{\mathcal{P}}{\rightarrow} \mu.
>$$

>[!important] Feller's Weak Law of Large Numbers (WLLN)
>Suppose $\left\{ X_{n},  n \ge 1 \right\}$ are **independent identically distributed (i.i.d.)** random variables with 
>- $$ \lim_{ x \to \infty }x\,\mathcal{P}\left[ |X_{1}| > x \right]  =0.$$ 
>
>Then as $n\to \infty$, 
>$$
>\frac{1}{n} S_{n} -  \mathbb{E}\left[ X_{1} \mathbb{1}\left\{ |X_{1}| \le n \right\}  \right] \stackrel{\mathcal{P}}{\rightarrow} 0.
>$$


## Explanation





-----------
##  Recommended Notes and References

- [[Kolmogorov Strong Law of Large Numbers]]

- [[Independent Random Variables]]
- [[Expectation of Random Variable]]
- [[Empirical Process and Empirical Measure]]
- [[Random Element and Random Variable]]

- [[Algorithm Big-O Notations in Probability]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]