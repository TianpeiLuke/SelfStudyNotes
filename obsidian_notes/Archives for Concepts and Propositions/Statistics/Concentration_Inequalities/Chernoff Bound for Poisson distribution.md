---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - chernoff_inequality
  - poisson_distribution
  - poisson_bound
topics:
  - statistics
name: Chernoff Bound for Poisson distribution
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**: Chernoff Bound for Poisson Distribution

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

## Chernoff Bound for Poisson Distribution

>[!important] Chernoff Bound for Poisson distribution
>Let $X$ be a **Poisson random variable** with *parameter $\nu$*, that is,  for all $k = 0, 1, 2, \ldots$,
>$$\mathcal{P}\{X = k\} = \frac{1}{k!}e^{–\nu}\nu^k.$$ 
>
>
>Let $Z = X - \nu$ be the corresponding *centered variable*. Then by direct calculation,
>$$
> \begin{align*}
> \psi_Z(\lambda) = \nu \left( e^{\lambda} - \lambda - 1 \right) ,\, \quad \lambda_t = \log\left(1 + \frac{t}{\nu}\right)
> \end{align*} 
> $$
>Therefore **the Legendre transform** equals, for every **$t > 0$**,
>$$
> \begin{align*}
> \psi_{Z}^{*}(t) &= \nu h\left(\frac{t}{\nu}\right),
> \end{align*}
>$$
>where the function $h$ is defined, for all  **$x \ge -1$**, by $$h(x) = (1 + x) \log(1 + x) - x.$$
>Similarly, for every **$t \le \nu$**,
>$$
> \begin{align*}
> \psi_{-Z}^{*}(t) &= \nu h\left(-\frac{t}{\nu}\right).
> \end{align*} 
>$$ 
>
>Thus by **Chernoff bound**, for every **$t > 0$**, the right-tail bound is 
>$$
> \begin{align*}
> \mathcal{P}\set{Z \ge t } \le \exp\left( - \nu h\left(\frac{t}{\nu}\right) \right).
> \end{align*}
>$$
>Similarly, for every **$t \le \nu$**, the left-tail bound is 
>$$
> \begin{align*}
> \mathcal{P}\set{-Z \ge  t} \le \exp\left( - \nu h\left(-\frac{t}{\nu}\right) \right).
> \end{align*}
>$$

- [[Poisson Random Variable]]


>[!info]
>The Chernoff bound for Poisson distribution is also widely seen in *sub-exponential distributions* with **heavy tails**. Thus the tail bound of the above form is called the **Poisson tail**. 

- [[Moment Generating Function]]

>[!info] Proof
> $$
> \begin{align*}
> \psi_X(\lambda) &= 
> \end{align*}
> $$
> 
> Then 
> $$
> \begin{align*}
> \lambda t - \psi_X(\lambda) &=  \\
> \frac{d}{d \lambda} \Big|_{\lambda_{t}^{*}} (\lambda t - \psi_{X}(\lambda))&= 0\\
> \end{align*}
> $$



>[!info] 
>The rate function of *Poisson distribution* is 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) &= \nu h\left(\frac{t}{\nu}\right), \;\; t >0 \\
> \text{where  } & h(x) = (1 + x) \log(1 + x) - x.
> \end{align*}
>$$ 



## Explanation

>[!info]
>By the Chernoff bound, we see that the **tail probability** decays in **exponential** rate.
>$$
> \mathcal{P}\set{X \ge t + \nu} = O \left(e^{- \nu h\left(\frac{t}{\nu}\right)}\right), \quad t \ge 0
>$$ 
>This implies that the Poisson distribution has *heavier tails* compared to Gaussian distribution. 

## Bernstein’s Inequality for Poisson Distribution

>[!important]
>The following important **inequality** can be used
>$$
>h(x) = (1+x)\log(1+x) - x \ge \frac{x^2}{2(1+ x/3)}
>$$

>[!info] 
>Thus 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) = \nu h\left(\frac{t}{\nu}\right) &\ge \nu \frac{ t^2 / \nu^2 }{2 \left(1+ (t / 3 \nu) \right) } \\
> &=  \frac{ t^2 }{2 \left( \nu +  t / 3 \right) }
> \end{align*}
>$$

>[!important] Bernstein’s Inequality for Poisson distribution
>Let $Z = X - \nu$ be the corresponding *centered Possion variable*. For all $t > 0$, 
>$$
> \begin{align*}
> \mathcal{P}\left[ Z \ge t\right] &\le \exp\left( - \psi_{Z}^{*}(t)  \right)\\
> &\le \exp\left( - \frac{ t^2 }{2 \left( \nu +  t / 3 \right) } \right)
> \end{align*}
>$$

- This is the **Bernstein's inequality**. 
- [[Bernstein Inequality]]

## Generalization

>[!info]
>Poisson random variable is a **sub-Gamma random variable.**





-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]
- [[Independent Random Variables]]

- [[Concentration Inequalities by Boucheron]]