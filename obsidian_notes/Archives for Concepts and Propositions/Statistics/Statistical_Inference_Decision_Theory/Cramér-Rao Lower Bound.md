---
tags:
  - concept
  - statistics/estimation
keywords:
  - cramer_rao_lower_bound
topics:
  - statistics/estimation
name: Cramér-Rao Lower Bound
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Cramér-Rao Lower Bound

>[!important] Theorem (Cramér-Rao Lower Bound)
>Let $X = (X_{1} \,{,}\ldots{,}\,X_{n})$ be a sample from $\mathcal{P} \in \mathscr{P}_{\Theta} := \left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$, where $\Theta \subset \mathbb{R}^d$ is an *open subset*.
>
>Suppose that $T(X)$ is an **estimator** with $$ \mathbb{E}_{\mathcal{P}_{\theta}}\left[ T(X) \right] = g(\theta)$$ being a **differentiable function** of $\theta$. 
>
>- That is, the p.d.f. with respect to $\mu$, $$f_{\theta} = \frac{d\mathcal{P}_{\theta}}{d\mu}$$ is *differentiable* as a function of $\theta$. 
>- And it satisfies **regularity condition** $$\frac{ \partial  }{ \partial \theta}\int h\,f_{\theta}\,d\mu = \int h\,\frac{ \partial  }{ \partial \theta }f_{\theta}\,d\mu, \quad \theta \in \Theta,$$ for $h(x) = 1$ and $h(x)= T(x)$.
>
>Then the **variance of estimator** satisfies 
>$$
>\begin{align*}
> \text{Var}\left( T(X) \right) &\ge \left[\frac{\partial}{ \partial \theta}g(\theta)\right]^T\,\left[ I(\theta)\right]^{-1}\,  \left[\frac{\partial}{ \partial \theta}g(\theta)\right],
>\end{align*}
>$$
>where 
>$$
>\begin{align*}
> I(\theta) =  \mathbb{E}_{\mathcal{P}_{\theta}}\left[\frac{\partial}{ \partial \theta}\log f_{\theta}(X)\, \left[ \frac{\partial}{ \partial \theta}\log f_{\theta}(X) \right]^{T}  \right],
>\end{align*}
>$$
>is the **Fisher information matrix**, which is assumed to be *positive definite* for any $\theta\in \Theta.$

^71591b

- [[Point Estimator]]
- [[Parametric Models]]
- [[Probability Density Function of Random Variable]]
- [[Likelihood Function]]
- [[Bias of Point Estimator and Unbiasedness]]
- [[Fisher Information]]
- [[Positive Semidefinite Operator]]

>[!important] Definition
>The inequality
>$$
>\begin{align*}
> \text{Var}\left( T(X) \right) &\ge \left[\frac{\partial}{ \partial \theta}g(\theta)\right]^T\,\left[ I(\theta)\right]^{-1}\,  \left[\frac{\partial}{ \partial \theta}g(\theta)\right],
>\end{align*}
>$$
>is called **information inequality** or the **Cramér-Rao lower bound**. 

>[!important] Cramér-Rao Lower Bound (Variance-Covariance version)
>The **variance-covariance matrix** $\text{Cov}(T, T)$ of an **unbiased estimator** $T(X)$ of $\theta$ satisfies
>$$
>\text{Cov}(T, T) \succeq \left[ I(\theta) \right]^{-1} 
>$$
>in the sense that 
>$$
>\text{Cov}(T, T) - \left[ I(\theta) \right]^{-1} 
>$$
>is **positive semi-definite**.




## Explanation

>[!important]
>The **Cramér-Rao lower bound** is attained if and only if $f_{\theta}$ is in an **exponential family**.

- [[Exponential Family of Distributions]]

>[!quote]
>In fact, if the **equality** above  holds for an *unbiased estimator* $T(X)$ of $g(\theta)$ (which is then a **UMVUE**), then the **greater** the *Fisher information* $I(\theta)$ is, the **smaller** $\text{Var}(T(X))$  is. 
>
>Thus, $I(\theta)$ is a **measure** of the **information that $X$ contains about the unknown $\theta$**.
>
>-- [[Mathematical Statistics by Shao]] pp 170






-----------
##  Recommended Notes and References




- [[Concepts and Theorems in Information Theory]]


- [[Mathematical Statistics by Shao]] pp 169
- [[All of Statistics A Concise Course by Wasserman]]
- [[Elements of Information Theory by Cover]]
- Wikipedia [Cramer-Rao Bound](https://en.wikipedia.org/wiki/Cram%C3%A9r%E2%80%93Rao_bound)
