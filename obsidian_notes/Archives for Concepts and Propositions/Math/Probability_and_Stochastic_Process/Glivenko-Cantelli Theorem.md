---
tags:
  - concept
  - math/probability
keywords:
  - glivenko_cantelli_theorem
  - cumulative_distribution_function
topics:
  - probability
name: Glivenko-Cantelli Theorem
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Glivenko-Cantelli Theorem

>[!important] Glivenko-Cantelli Theorem
>Let $\left\{ X_{n}, n \ge 1 \right\}$ be an **independent identically distributed (i.i.d.)** sequence of random variables with common *cumulative distribution function* $F(x)$.
>
>Define the **empirical distribution function** as
>$$
>\hat{F}_{n}(x, \omega) = \frac{1}{n}\sum_{j=1}^{n}\mathbb{1}\left\{ \omega: X_{j}(\omega) \le x \right\}. 
>$$
>
>Then $\hat{F}_{n}$ converges to $F$ **uniformly** for all $x$ as $n\to \infty.$
>
>That is, 
>$$
>\sup_{x}|\hat{F}_{n}(x) - F(x)| \stackrel{a.s.}{\longrightarrow} 0
>$$
>

- [[Cumulative Distribution Function of Random Variable]]
- [[Kolmogorov Strong Law of Large Numbers]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Weak Convergence in Banach Space]]

>[!important]
>In [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]], the Glivenko-Cantelli theorem is also called **the Uniform Law of Large Numbers**.

## Explanation

>[!info]
>Note that
>$$
> \mathbb{E}_{ \mathcal{P} }\left[ \hat{F}_{n}(x) \right] = \frac{1}{n}\sum_{j=1}^{n}\mathcal{P}\left\{ X_{j} \le x \right\} = \mathcal{P}\left\{ X \le x \right\}  = F(x)
>$$
>
>By SLLN, for each $x\in \mathcal{X}$ fixed, the empirical distribution function $\hat{F}_{n}(x)$ converges to $F(x)$ almost surely. 
>
>However, Glivenko-Cantelli Theorem is stronger as it is the **weak convergence in space of functions**, or **uniformly almost everywhere convergence**
>$$
>F_{n} \stackrel{w}{\longrightarrow} F.
>$$

- [[Uniformly Almost Everywhere Convergence]]
- [[Weak Convergence in Banach Space]]


>[!important]
>This theorem motivates our study in **empirical process**. 

>[!important] Glivenko-Cantelli Theorem (Empirical Process)
>
>Specifically, let $\mathcal{F} := \left\{ \mathbb{1}\left\{ \cdot \le x \right\}, \; x \in \mathcal{X} \right\}$ be a family to measurable functions. The  *Glivenko-Cantelli Theorem* states that
>$$
>\sup_{f \in \mathcal{F}}\left\lvert \mathcal{P}_{n}f  - \mathcal{P}f\right\rvert \to 0
>$$
>where the **empirical measure**
>$$
>\mathcal{P}_{n} := \frac{1}{n}\sum_{j=1}^n \delta_{X_{j}}
>$$
>and for $f\in \mathcal{F}$, i.e. $f_{x}(y) := \mathbb{1}\left\{ y \le x \right\}$
>$$
>\mathcal{P}_{n}f := \frac{1}{n}\sum_{j=1}^n  \mathbb{1}\left\{ X_{j} \le x \right\}. 
>$$

- [[Integral Probability Metric between Probability Measures]]
- [[Glivenko-Cantelli Class]]


## Corollary







-----------
##  Recommended Notes and References


- [[Uniformly Almost Everywhere Convergence]]
- [[Weak Convergence in Banach Space]]

- [[Cumulative Distribution Function of Random Variable]]
- [[Kolmogorov Strong Law of Large Numbers]]

- [[Empirical Process and Empirical Measure]]

- [[Independent Random Variables]]
- [[Expectation of Random Variable]]
- [[Empirical Process and Empirical Measure]]
- [[Random Element and Random Variable]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]