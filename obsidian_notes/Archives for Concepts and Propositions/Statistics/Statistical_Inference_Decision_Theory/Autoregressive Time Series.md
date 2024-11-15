---
tags:
  - concept
  - statistics/inference
  - statistics/estimation
keywords:
  - autoregressive_time_series
topics:
  - statistics/inference
  - statistics/estimation
name: Autoregressive Time Series
date of note: 2024-11-14
---

## Concept Definition

>[!important]
>**Name**: Autoregressive Time Series

>[!important] Definition
>The **first order autoregressive time series** or **AR(1)** is defined as
>$$
>X_{t} = \beta\,X_{t-1} + U_{t}\, \quad t=2\,{,}\ldots{,}\,T
>$$
>where
>- $U_{t} \sim \mathcal{N}(0,1)$ are i.i.d 
>- and $\beta$ is an unknown parameter satisfying $$\lvert \beta \rvert < 1$$
>- and assume that $$X_{1} \sim \mathcal{N}(0, \sigma^2).$$

^36ea9a

- [[Markov Chain and Markov Process]]
- [[Martingale]]

>[!important] Definition
>The **$p$-th order autoregressive time series** or **AR(p)** is defined as
>$$
>X_{t} = \sum_{i=1}^{p}\beta_{i}\,X_{t-i} + U_{t}\, \quad t=2\,{,}\ldots{,}\,T
>$$
>where
>- $U_{t} \sim \mathcal{N}(0,1)$ are i.i.d 
>- and $\beta := (\beta_{1}\,{,}\ldots{,}\,\beta_{p})$ is an unknown parameters
>- and assume that $$X_{1} \sim \mathcal{N}(0, \sigma^2).$$

- [[Gaussian Random Variable]]

### Maximum Likelihood Estimation

>[!important] Definition
>Let $$\theta := (\beta, \sigma^2).$$ Let $\mathcal{D} := \left\{ x_{1} \,{,}\ldots{,}\, x_{T}\right\}$ be samples from the *AR(1) model.*
>
>The **log-likelihood function** is given by 
>$$
>\begin{align*}
>\ell(\theta) &:= - \frac{T}{2} \log(2\pi) - \frac{T}{2} \log \sigma^2 + \frac{1}{2}\log \left( 1- \beta^2 \right) \\[5pt]
>&\quad -\frac{1}{2\sigma^2}\left\{ (1- \beta^2) x_{1}^2 + \sum_{t=2}^{T}\left( x_{t} - \beta\,x_{t-1} \right)^2 \right\} 
>\end{align*}
>$$
>- The **conditional MLE** of $\beta$ *conditioned on* $X_{1}=x_{1}$  is given by $$\hat{\beta} := \frac{\sum_{t=2}^{T}\,\left( x_{t} - \bar{\mu}_{2:t} \right)\left( x_{t-1} - \bar{\mu}_{1: t-1} \right) }{\sum_{t=2}^{T}\,\left( x_{t-1} - \bar{\mu}_{1: t-1} \right)^2}$$ where the **moving average** of $x_{t}$ is given by $$\hat{\mu}_{1: t-1} := \frac{1}{T-1}\sum_{t=1}^{T-1}x_{t}, \quad \hat{\mu}_{2: t} := \frac{1}{T-1}\sum_{t=2}^{T}x_{t}$$
>-  The **conditional MLE** of $\sigma^2$ *conditioned on* $X_{1}=x_{1}$   is given by $$\hat{\sigma}^2 = \frac{1}{T-1}\sum_{t=2}^{T}\left[ x_{t} - \hat{\mu}_{2:t} - \hat{\beta}\left( x_{t-1} -  \hat{\mu}_{1:t-1} \right) \right]^2$$

- [[Maximum Likelihood Estimation]]


## Explanation





-----------
##  Recommended Notes and References


- [[Autoregressive Models]]

- [[An Introduction to Bootstrap by Efron]] pp 92 - 98
- [[Theory of Point Estimation by Lehmann]] pp. 481
- [[Mathematical Statistics by Shao]] pp 45-46, 85, 285-286