---
tags:
  - concept
  - math/stochastic_process
keywords:
  - quadratic_variation
  - martingale
  - covariantion
topics:
  - stochastic_process
name: Quadratic Variation and Covariation of Martingale
date of note: 2024-06-13
---

## Concept Definition

>[!important]
>**Name**: Quadratic Variation and Covariation of Stochastic Process

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. Suppose $(X_{t}, t \ge 0)$ is a real-valued *stochastic process*. 
>
>The **quadratic variation** of $X_{t}$ is defined as
>$$
>\begin{align*}
> \left[ X, X \right]_{t} := \lim_{ \Delta(P_{t}^n) \to 0 }\sum_{i=0}^{k_{n}-1}\left(X_{t_{i+1}^n} - X_{t_{i}^n}\right)^2 
>\end{align*}
>$$
>where 
>- $P_{t}^n = (t_{0}^n, \,{,}\ldots{,}\, t_{k_{n}}^n)$ is a **partition** on $[0,t]$, and $t_{0}^n =0$ and $t_{k_{n}}^n = t.$
>- $$\Delta(P_{t}^n) \equiv \sup_{0\le i\le k_{n}-1}\lvert t_{i+1}^n - t_{i}^n \rvert $$ is the *norm of the tagged partition*. 

- [[Itô Stochastic Integration]]
- [[Riemann Integration]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 198

>[!important] Definition
>The **covariation** (or **cross-variance**) of two stochastic processes $X_{t}$ and $Y_{t}$ is defined as
>$$
>\begin{align*}
> \left[ X, Y \right]_{t} := \lim_{ \Delta(P_{t}^n) \to 0 }\sum_{i=0}^{k_{n}-1}\left(X_{t_{i+1}^n} - X_{t_{i}^n}\right)\left(Y_{t_{i+1}^n} - Y_{t_{i}^n}\right) 
>\end{align*}
>$$
>where 
>- $P_{t}^n = (t_{0}^n, \,{,}\ldots{,}\, t_{k_{n}}^n)$ is a **partition** on $[0,t]$, and $t_{0}^n =0$ and $t_{k_{n}}^n = t.$
>- $$\Delta(P_{t}^n) \equiv \sup_{0\le i\le k_{n}-1}\lvert t_{i+1}^n - t_{i}^n \rvert $$ is the *norm of the tagged partition*. 

### Stochastic Differential of Covariation

>[!important] 
>By definition above, the **stochastic differential** representation of the **covariation** is 
>$$
>\begin{align*}
>d\left[ X, Y \right] = dX\,dY.
>\end{align*}
>$$
>Similarly, the *stochastic differential* of the **quadratic variation** is
>$$
>\begin{align*}
>d\left[ X, X \right] = (dX)^2.
>\end{align*}
>$$

- [[Stochastic Differential]]

## Explanation

>[!info]
>The **quadratic variation** of stochastic process can be seen as proportional to the **variance of increment** of the stochastic process.
>
>For *time-homogeneous discrete time stochastic process* $X_{n}, n=1,\,{,}\ldots{,}\,$,  $$\Delta X_{i} := X_{i+1} - X_{i}$$ are i.i.d. samples, and
>$$
>\left[ X, X \right]_{n} := \sum_{i=1}^{n-1}\left(X_{i+1} - X_{i}\right)^2 = n\;\text{Var}(\Delta X_{i})
>$$

>[!info]
>The **covariation** of two stochastic processes can be seen as proportional to the **covariance of increment** of the stochastic process.
>
>For *time-homogeneous discrete time stochastic process* $(X_{n}, n=1,\,{,}\ldots{,}\,)$, and   $(Y_{n}, n=1,\,{,}\ldots{,}\,)$ $$\Delta X_{i} := X_{i+1} - X_{i}, \quad \Delta Y_{i} := Y_{i+1} - Y_{i}$$ are i.i.d. samples, and
>$$
>\left[ X, Y \right]_{n} := \sum_{i=1}^{n-1}\left(X_{i+1} - X_{i}\right)\left(Y_{i+1} - Y_{i}\right) = n\;\text{Cov}(\Delta X_{i}\, \Delta Y_{i})
>$$


## Martingale

>[!important] Proposition
>Let $X_{t}$ be a **martingale** with **finite second moments**, $$\mathbb{E}_{ p }\left[  X_{t}^2 \right] < \infty$$ for all $t$. 
>
>Then 
>- the **quadratic variation** of $X_{t}$, $\left[ X, X \right]_{t}$, *exists*.
>- Moreover, $$X^2_{t} - \left[ X, X \right]_{t}$$ is a **martingale**.

- [[Martingale]]

>[!important] Proposition
>Let $X_{t}$ be a **local martingale**.
>
>Then 
>- the **quadratic variation** of $X_{t}$, $\left[ X, X \right]_{t}$, *exists*.
>- Moreover, $$X^2_{t} - \left[ X, X \right]_{t}$$ is a **local martingale**.

- [[Local Martingale]]

## Stochastic Integration

>[!important]
>Let $$dY = X_{t}\,dW.$$ $Y$ is a **local martingale**. Its **quadratic variation** is given by
>$$
>\begin{align*}
> \left[ Y, Y \right]_{t} &= \int_{0}^{t}\,X^2_{s}\,ds
>\end{align*}
>$$

>[!info]
>Use the fact that
>$$(dW)^2 = dt$$
>
>Then 
>$$
>\begin{align*}
>d \left[ Y, Y \right] &= \left( dY \right)^2\\
>&= \left( X\,dW \right)^2 \\
>&= X^2\,dt
>\end{align*}
>$$


>[!important]
>Let
>$$
>\begin{align*}
>dX_{1} &= F_{1}\,dt + G_{1}\,dW\\
>dX_{2} &= F_{2}\,dt + G_{2}\,dW
>\end{align*}
>$$
>Then the **covariation** of two *Ito diffusions* are
>$$
>\left[ X_{1}, X_{2} \right]_{t} = \int_{0}^{t}\,G_{1}\,G_{2}\,ds
>$$

- [[Itô Product Rule and Stochastic Integration by Parts]]




-----------
##  Recommended Notes and References

- [[Lévy Characterization of Brownian Motion]]
- [[Itô Product Rule and Stochastic Integration by Parts]]
- [[Itô Stochastic Integration]]

- [[Riemann Integration]]
- [[Total Variation of Function]]


- [[Introduction to Stochastic Calculus by Klebaner]] pp 198
- Wikipedia [Quadratic_variation](https://en.wikipedia.org/wiki/Quadratic_variation)