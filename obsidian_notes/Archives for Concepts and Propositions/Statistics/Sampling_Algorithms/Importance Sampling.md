---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - importance_sampling
topics:
  - statistics/monte_carlo
name: Importance Sampling
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Importance Sampling

![[Accept-Reject Sampling#^c0ddd8]]

- [[Accept-Reject Sampling]]

>[!info]
> The vanilla rejection sampling method suffers from **low sample efficiency** and **slow convergence** since it wasted a lot effort evaluating random samples located in regions where the target function value $h(x)p(x)$ is almost zero. 

>[!important] Definition
>Let $\mathcal{P}$ be a probability distribution of random variable $X \in \mathcal{X}$ and $(\mathcal{X}, \mathscr{F})$ is a measurable space. 
>
>The **fundamental principle** of **important sampling** states that in order to compute the  *expectation* of a measurable function $h$ with respect to $\mathcal{P}$,  it is sufficient to apply a *trial probability distribution* $\mathcal{Q}$ that is *dominating* $\mathcal{P}$, i.e.,  $$\mathcal{P} \ll \mathcal{Q},$$ and the target expectation can be found by 
>$$
>\begin{align*}
> \mathbb{E}_{ \mathcal{P} }\left[ h(X) \right] &= \mathbb{E}_{ \mathcal{Q} }\left[ h(X) \,\frac{d\mathcal{P}}{d\mathcal{Q}} (X) \right] \\[5pt]
> &:= \mathbb{E}_{ \mathcal{Q} }\left[ h(X) \,w(X) \right],
>\end{align*}
>$$
>where the **importance weight function** $w$ is defined as the *Radon-Nikodym derivative* of $\mathcal{P}$ with respect to $\mathcal{Q},$ i.e. $$w(x) = \frac{d\mathcal{P}}{d\mathcal{Q}}(x), \quad x\in \mathcal{X}.$$
>
>If $p(x)$ and $q(x)$ are p.d.f. for $\mathcal{P}$ and $\mathcal{Q}$ with respect to a common nominating $\sigma$-finite measure $\nu$, then 
>$$
>w(x) = \frac{d\mathcal{P} / d\nu}{d\mathcal{Q} / d\nu}= \frac{p(x)}{q(x)}.
>$$

^1fa755

- [[Expectation of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Absolute Continuity for Measures]]
- [[Radon-Nikodym Derivative]]
- [[Lebesgue-Radon-Nikodym Theorem]]


>[!important] Definition
>Consider the task of estimating the expecation
>$$
>\mu =  \mathbb{E}_{ p }\left[ h(X) \right].
>$$
>
>The **Importance Sampling Algorithm** is described as below:
>- Draw $$X_1, \ldots, X_{m} \sim g(x)$$ where $g$ is **trial p.d.f.**;
>- Calculate **the importance weight** $w(x)$:
>$$
> \begin{align*}
> w_i := w(X_i) &= \frac{p(X_i)}{g(X_i)}, \quad i=1,\ldots, m
> \end{align*}
>$$ 
>- **Approximate** $\mu$ by $$\hat{\mu}_{m}^{(1)} = \frac{\sum_{i=1}^{m}w_i\,h(X_i)}{\sum_{i=1}^{m}w_i}$$ or we can use the **unbiased** estimator $$\hat{\mu}_{m}^{(2)} = \frac{1}{m}\sum_{i=1}^{m}w_i\,h(X_i)$$ 
>
>The normalized estimator is **biased** but as $\hat{\mu}_{m}^{(1)}\rightarrow \mu$, i.e. it is **asymptotically unbiased**.

## Explanation

>[!important]
>The **importance sampling** idea suggests that one should **focus on regions of "importance"** so as to *save computational resources*. 
>
>It is important to note that in high dimensional space, the *support* of the target distribution is *exponentially small* as compared to the entire region $\mathcal{X}$. 
>
>In **high dimensional** setting, the *vanilla Monte Carlo methods* are bound to **fail**.

## Sequential Importance Sampling

- [[Sequential Importance Sampling]]


## Nonlinear Filters

- [[Kalman Filter Discrete-Time]]
- [[Particle Filter or Sampling-Importance-Resampling]]




-----------
##  Recommended Notes and References





- [[Markov Chain Monte Carlo Methods]]

- [[All of Statistics A Concise Course by Wasserman]] pp 408
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 31 - 50
- [[Monte Carlo Statistical Methods by Robert]] pp 91, 92, 203, 268, 546

- [[Reinforcement Learning An Introduction by Sutton]] pp 103 - 117

- [[Probabilistic Graphical Models by Koller]] pp 494
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]] pp 583 - 585
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429