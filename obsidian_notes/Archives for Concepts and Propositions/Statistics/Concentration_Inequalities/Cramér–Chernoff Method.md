---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - chernoff_inequality
  - moment_generating_function
  - legendre_transform
topics:
  - statistics
  - information_theory
name: Cramér–Chernoff Method
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Cramér–Chernoff's Method

>[!info]
>Let $\phi: I \subseteq \mathbb{R} \to \mathbb{R}$ be any *nondecreasing and nonnegative* function, and if $X$ denotes a random variable taking values in $I$,  then *Markov’s inequality* implies that for every $t \in I$ with $\phi(t) > 0,$
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] \le \mathcal{P}\left[\phi(X) \ge \phi(t)\right] &\le  \frac{\mathbb{E}\left[\phi(X)  \right]}{\phi(t)}.
> \end{align*}
> $$

>[!info]
>Set $\phi(x) = e^{\lambda x}$,  for $I = (-\infty, +\infty)$, and $\lambda > 0$, we obtain the Chernoff's inequality

>[!important]
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X$ is a *random variable* whose *moment generating function* 
>$$
>M_{X}(\lambda) := \mathbb{E}\left[ e^{\lambda X} \right] < \infty.
>$$
> Then for all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ X \ge t\right] &\le \inf_{\lambda \ge 0} \frac{ \mathbb{E}\left[ e^{\lambda X} \right] }{e^{\lambda t}} \\
> &= \inf_{\lambda \ge 0}\exp \left( - \lambda t + \log \mathbb{E}\left[ e^{\lambda X} \right] \right) \\
> &= \exp \left( \sup_{\lambda \ge 0}\{  - \lambda t + \log \mathbb{E}\left[ e^{\lambda X} \right]  \} \right) 
> \end{align*}
> $$

- [[Moment Generating Function]]
## Chernoff's Inequality

>[!info]
>Define the *logarithm* of **the moment-generating function** as 
> $$
> \begin{align*}
> \psi_{X}(\lambda) := \log M_{X}(\lambda) = \log \mathbb{E}\left[ e^{\lambda X} \right], \quad \lambda \ge 0.
> \end{align*}
> $$
> 
> - Note that $\psi_{X}$ is a *convex function* of $\lambda$.
> 

- [[Moment Generating Function]]

>[!info]
>Introduce **the Legendre transform** of $\psi_{X}(\lambda)$ as
>$$
>\begin{align*}
>\psi_{X}^{*}(t) &:= \sup_{\lambda \ge 0}\left( \lambda t - \psi_{X}(\lambda) \right) \\
>&=\sup_{\lambda \ge 0}\left( \lambda t - \log \mathbb{E}\left[ e^{\lambda X} \right] \right)
\end{align*}
>$$

>[!info]
>The above transform is also called the **Cramér transform** of *random variable* $X$.

- [[Moment Generating Function]]
- [[Legendre Transform]]
- [[Convex Conjugate Function]]


- We can obtain *Chernoff's inequality*

>[!important] Chernoff's inequality
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

> [!info]
>This condition is *stronger* than Markov inequality, since in order for *the moment generation function being finite*, the random variable must have **moments of every order**.

## The Sum of I.I.D Samples

>[!info]
>- $\psi_{X}^{*}$ is called **the rate function** in the **Large Deviation Theory**.
>- The Chernoff's inequality is the key for the Cramér theorm, which determines the *tail probabilities* of sums of i.i.d samples 


>[!important] Theorm (Chernoff's inequality, I.I.D Cases)
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be $n$ i.i.d *random variables* whose *moment generating function* 
>$$
>M_{X_{i}}(\lambda) := \mathbb{E}\left[ e^{\lambda X_{i}} \right] < \infty.
>$$
> Then for all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ \sum_{i=1}^n X_{i}  \ge t\right] &\le \exp\left( - n \psi_{X}^{*}\left( \frac{t}{n} \right)  \right)
> \end{align*}
> $$

>[!info]
>Note that for $S_{n} := \sum_{i=1}^n X_{i}$ and $X_{i}$ are i.i.d, so the expectation are the same.
> $$
> \psi_{S_{n}}(\lambda) = \log M_{S_{n}}(\lambda) := \log \mathbb{E}\left[ e^{\lambda S_{n}} \right] = n\, \psi_{X_{1}}(\lambda)
> $$
> So
> $$
> \psi^{*}_{S_{n}}(t) = \left( n\, \psi_{X_{1}}(\lambda)  \right)^{*} = n \psi_{X_{1}}^{*}\left( \frac{t}{n} \right)
> $$


>[!important] Cramér Theorm (Asymptotic Version)
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be $n$ i.i.d *random variables* whose *moment generating function* 
>$$
>M_{X_{i}}(\lambda) := \mathbb{E}\left[ e^{\lambda X_{i}} \right] < \infty.
>$$
> Then 
> $$
> \begin{align*}
> \lim_{ n \to \infty } \frac{1}{n} \log \left( \mathcal{P}\left[ \sum_{i=1}^n X_{i}  \ge n t\right] \right)  &= -  \psi_{X}^{*}\left( t \right)  
> \end{align*}
> $$
> for all $x >  \mathbb{E}_{}\left[ X_{i} \right]$.

>[!info]
>The Cramér theorem said that the distribution of the sum of i.i.d. random variables *satisfy a large deviation principle* with **rate function $\psi_{X}^{*}.$**

- [[Independent Random Variables]]
## Generalization

>[!info]
>Note that $e^x$ is a *convex function*, and by *Jenson's inequality*, 
>$$
>\psi_{X}(\lambda) := \log \mathbb{E}\left[ e^{\lambda X} \right] \ge \lambda  \mathbb{E}\left[ X \right]
>$$ 
>Therefore, for all *negative values* of $\lambda$,  $λt – \psi_{X}(\lambda) \le 0$ whenever $t \ge \mathbb{E}\left[X\right].$
>
>This means we can extend $\lambda \ge 0$ to $\lambda \in \mathbb{R}$ in definition of $\psi_{X}^{*}$
> $$
> \psi_{X}^{*}(t) = \sup_{\lambda \in \mathbb{R}}\left( \lambda t - \log \mathbb{E}\left[ e^{\lambda X} \right] \right)
> $$
>
>This function is called the **Fenchel–Legendre dual function** of $\psi_{X}$.



>[!info]
>For every $t \ge \mathbb{E}\left[X\right]$, the **Cramér transform** $\psi_{X}^{*}(t)$ coincides with the **Fenchel–Legendre dual function**.


## Computing Optimal $\lambda_{t}^{*}$ and value of Legendre transform

>[!info]
> - Differentiability of $\psi_{X}$ implies that the optimal solution $\lambda_{t}^{*}$ to the Legendre transform can be computed by **differentiating $\lambda t - \psi_{X}(\lambda)$ with respect to $\lambda$**.
> $$
> \begin{align*}
> \frac{d}{d \lambda} \Big|_{\lambda_{t}^{*}} (\lambda t - \psi_{X}(\lambda))&= 0\\
> \implies  \psi_{X}^{'}(\lambda_{t}^{*}) &= t
> \end{align*}
> $$
> - $\psi_{X}(\lambda)$ is *strictly convex*, thus its *differential is monotone increasing*, so it has monotone increasing inverse $(\psi_{X}^{'})^{-1}$. So
> $$
> \lambda_{t}^{*} = (\psi_{X}^{'})^{-1}(t)
> $$
> - Thus the value of Legendre transform is
> $$
> \psi_{X}^{*}(t) = \lambda_{t}^{*} t - \psi_{X}(\lambda_{t}^{*}) = t\,(\psi_{X}^{'})^{-1}(t) - t
> $$
> 



-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Markov Inequality]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]
  
- Wikipedia [Chernoff bound](https://en.wikipedia.org/wiki/Chernoff_bound)

