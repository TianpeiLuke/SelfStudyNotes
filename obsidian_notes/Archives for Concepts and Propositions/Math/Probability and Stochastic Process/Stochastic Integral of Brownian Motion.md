---
tags:
  - concept
  - math/stochastic_process
keywords:
  - stochastic_integral_brownian_motion
topics:
  - stochastic_process
name: Itô Stochastic Integral of Brownian Motion
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Stochastic Integral of Brownian Motion


[[Itô Chain Rule and Itô Formula]]


>[!important]
>Let $X_{t} := W_{t}$, $u(x) = x^m$. Then $$dX = dW \implies F \equiv 0 \text{ and } G \equiv 1.$$
>
>By [[Itô Chain Rule and Itô Formula]],
>$$
>d(W^m) = m\,W^{m-1}\,dW + \frac{m(m-1)}{2}\,W^{m-2} dt
>$$
>Let $m=2$
>$$
>d(W^2) = 2W\,dW + dt
>$$
>Equivalently, 
>$$
>\begin{align*}
>\int_{s}^{t}W\,dW =\frac{ W^2(t) - W^2(s)}{2} - \frac{t-s}{2}
>\end{align*}
>$$

- [[Itô Stochastic Integration]]
- [[Brownian Motion Wiener Process]]

>[!important]
>Two simple stochastic differentials
>- $$d(W^2) = 2W\,dW + dt$$
>- $$d(tW) = W\,dt + t\,dW$$



## Expansion

>[!important]
>Compare with normal **Riemann–Stieltjes integral**
>$$
>\int_{s}^t W(u)\,dW(u) = \frac{ W^2(t) - W^2(s)}{2}, 
>$$
>we see additional term
>$$
>c(t, s) = -\frac{t-s}{2}
>$$
>Intuitively, this is due to $$dW \approx (dt)^{1 / 2}$$

- [[Riemann–Stieltjes Integration]]


-----------
##  Recommended Notes and References


- [[Itô Stochastic Integration]]
- [[Itô Stochastic Integration of Step Process]]
- [[Brownian Motion Wiener Process]]



- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]