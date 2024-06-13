---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - chernoff_inequality
  - gaussian_distribution
  - gaussian_bound
topics:
  - statistics
name: Chernoff Bound for Gaussian Distribution
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**: Chernoff Bound for Gaussian Distribution

>[!info] Chernoff's inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X$ is a *random variable* whose *moment generating function* 
>$$
>M_{X}(\lambda) := \mathbb{E}\left[ e^{\lambda X} \right] < \infty.
>$$
> Then for all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ X \ge t\right] &\le \exp\left( - \psi_{X}^{*}(t)  \right)
> \end{align*}
> $$
> where $\psi_{X}^{*}(t)$ is **the Legendre transform** of $\psi_{X}(\lambda) := \log M_{X}(\lambda)$, the *logarithm* of *the moment-generating function*.

## Chernoff Bound for Gaussian Distribution

>[!important] Chernoff Bound for Normal distribution
>Let $X$ be a **centered Normal random variable** with variance $\sigma^2$. Then
>$$
> \begin{align*}
> \psi_X(\lambda) = \frac{\lambda^2 \sigma^2}{2},\, \quad \lambda_t = \frac{t}{\sigma^2}
> \end{align*} 
>$$
>and, therefore for every $t > 0$, 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) &= \frac{t^2}{2\sigma^2}.
> \end{align*} 
>$$ 
>Hence, **Chernoff's inequality** implies, for all $t > 0$,
>$$
> \begin{align*}
> \mathcal{P}\{X \ge t\} &\le \exp \left( -\frac{t^2}{2\sigma^2} \right).
> \end{align*}
>$$ 

- [[Gaussian Random Variable]]
- [[Moment Generating Function]]

>[!info] Proof
> $$
> \begin{align*}
> \psi_X(\lambda) &= \log \int_{\mathbb{R}} \exp\left( -\lambda x  \right) \frac{1}{\sqrt{ 2 \pi \sigma^2 }}\exp\left( - \frac{x^2}{2\sigma^2}  \right) dx\\
> &= \log \frac{1}{\sqrt{ 2 \pi \sigma^2}}\int_{\mathbb{R}} \exp\left( -\lambda x - \frac{x^2}{2\sigma^2}  \right)  dx \\
> &= \log \frac{1}{\sqrt{ 2 \pi \sigma^2}} \int_{\mathbb{R}}\exp\left( -\frac{1}{2\sigma^2} \left( x + 2\sigma^2  \lambda  \right)^2 + \frac{\lambda^2\sigma^2}{2} \right)  dx\\
> &= \log \frac{1}{\sqrt{ 2 \pi \sigma^2}} \exp\left(\frac{\lambda^2\sigma^2}{2}\right) \int_{\mathbb{R}}\exp\left( - \left( \frac{x + 2\sigma^2  \lambda}{ \sqrt{2} \sigma}  \right)^2  \right)  dx \\
> &= \log \frac{1}{\sqrt{ 2 \pi \sigma^2}}  \exp\left(\frac{\lambda^2\sigma^2}{2}\right) \sqrt{ 2 \pi \sigma^2} \\
> &= \log \exp\left(\frac{\lambda^2\sigma^2}{2}\right) \\
> &= \frac{\lambda^2\sigma^2}{2}
> \end{align*}
> $$
> 
> Then 
> $$
> \begin{align*}
> \lambda t - \psi_X(\lambda) &= \lambda t - \frac{\lambda^2\sigma^2}{2} \\
> \frac{d}{d \lambda} \Big|_{\lambda_{t}^{*}} (\lambda t - \psi_{X}(\lambda))&= 0\\
> t - \sigma^2 \lambda_{t}^{*} &= 0\\
> \lambda_{t}^{*}  &= \frac{t}{\sigma^2 }. \qquad Q.E.D.
> \end{align*}
> $$

>[!info] 
>The rate function of Gaussian is 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) &= \frac{t^2}{2\sigma^2}.
> \end{align*} 
>$$ 


## Explanation

>[!important]
>**Chernoff bound for Gaussian distribution** appears to be quite **sharp** in this case. In fact, one can show that it *cannot be improved uniformly* by more than a factor of $1/2.$


>[!info]
>By the Chernoff bound, we see that the **tail probability** decays in **super-exponential** rate.
>$$
> \mathcal{P}\{X \ge t\} = O\left( e^{-c t^2} \right)
>$$


## Generalization

>[!info]
>The Chernoff bound for Gaussian distribution is the basis for the similar bounds on a wide family of *sub-Gaussian distributions.*





-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]
- [[Independent Random Variables]]
- [[Concentration Inequalities by Boucheron]]