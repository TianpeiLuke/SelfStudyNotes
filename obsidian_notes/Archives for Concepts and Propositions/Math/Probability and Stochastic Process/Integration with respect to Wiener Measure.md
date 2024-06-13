---
tags:
  - concept
  - math/stochastic_process
keywords:
  - white_noise_integration
topics:
  - stochastic_process
name: Gaussian White Noise Integration
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: 


- [[Step Process]]
- [[Wiener Measure as Random Finitely Additive Measures]]

### Simple White Noise Integral



### White Noise Integral




## Explanation

>[!important] 
>This integration is **not** the **Itô stochastic integration**.
>
>Since the Wiener process
>$$
>W_{t} = \int_{-\infty}^{\infty}\mathbb{1}_{(-\infty, t]}\;d\mathcal{W}
>$$
>we have
>$$
>W_{t_{i+1}} - W_{t_{i}} =  \int_{-\infty}^{\infty}\mathbb{1}_{(t_{i}, t_{i+1}]}d\mathcal{W}
>$$
>Then the **Itô Stochastic Integration** of *step process* $(X_{t})$ with respect to Wiener process $(W_{t})$
>$$
>\begin{align*}
>\int_{0}^{T}X_{t}\,dW &= \sum_{i=0}^{n-1}X_{i}\left(W_{t_{i+1}} - W_{t_{i}}\right)\\
>&= \sum_{i=0}^{n-1}X_{i}\int_{-\infty}^{\infty}\mathbb{1}_{(t_{i}, t_{i+1}]}d\mathcal{W}\\
>&= \int_{-\infty}^{\infty}\left(\sum_{i=0}^{n-1}X_{i}\mathbb{1}_{(t_{i}, t_{i+1}]}\right)d\mathcal{W}
>\end{align*}
>$$
>
>This is different from the definition of **white noise integral** of simple function as
>$$
>\int_{-\infty}^{\infty}\left(\sum_{i=0}^{n-1}x_{i}\mathbb{1}_{(t_{i}, t_{i+1}]}\right)d\mathcal{W}
>$$
>where the **integrand** is a **simple function** $$f:= \sum_{i=0}^{n-1}x_{i}\mathbb{1}_{(t_{i}, t_{i+1}]}\in L^2(T, \mu)$$ not a **random variable**.


- [[Itô Stochastic Integration of Step Process]]


-----------
##  Recommended Notes and References

- [[Step Process]]
- [[Wiener Measure as Random Finitely Additive Measures]]


- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]
- [[White Noise Process]]


- [[Introduction to Stochastic Differential Equations by Evans]]