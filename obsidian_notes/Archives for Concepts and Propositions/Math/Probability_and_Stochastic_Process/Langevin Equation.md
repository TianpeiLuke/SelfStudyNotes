---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - langevin_equation
topics:
  - stochastic_process
name: Langevin Equation
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Langevin Equation

>[!important] Definition
>Let $(X(\cdot,t))$ be the *velocity* of *Brownian particles*. 
>
>The Brownian motion of particles under **frictional forces** is given by the following *stochastic differential equation*
>$$
>\left\{
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= X_{0}
>\end{align*}
>\right.
>$$
>
>The stochastic differential above is called **the Langevin equation**. 

^b373a8

- [[Stochastic Differential Equations]]
- [[Stochastic Differential]]
- [[Ito Stochastic Integration]]
- [[Brownian Motion Wiener Process]]

## Solution

>[!info]
>Let $n = m = 1$. Consider the following **linear stochastic differential equation**:
>$$
>\left\{ 
>\begin{align*}
>dX(t) &= f_{t}\,X_{t}\,dt + g_{t}\,X(t)\,dW\\
>X(0)&= 1
>\end{align*}
>\right.
>$$
>where both $f, g: [0,T] \to \mathbb{R}$ are a **continuous function** not a random variable.
>
>The solution is
>$$
>X_{t} := \exp\left(  \int_{0}^{t}\left(f - \frac{1}{2}g^2 \right)\,ds + \int_{0}^{t}g\,dW  \right)
>$$
>This solution is **unique**.


>[!important] Solution of Langevin Equation
>For *Langevin equation*, $f_{t} = -\beta$, and $g_{t}X_{t} = \sigma.$
>
>The **solution** of the *Langevin equation*
>$$
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= X_{0}
>\end{align*}
>$$
>is 
>$$
>X(t) = e^{-\beta\,t}\,X_{0} + \sigma\,\int_{0}^{t}e^{-\beta (t-s)}\,dW(s)
>$$

- [[Matrix Exponential]]
- [[Linear Stochastic Differential Equation Explicit Solution]]

>[!info]
>To verify, 
>$$
>\begin{align*}
>dX_{t} &= -\beta e^{-\beta t}\,X_{0}dt + \sigma (-\beta) e^{-\beta t}dt\int_{0}^{t}e^{\beta s}\,dW(s) + \sigma e^{-\beta t}\,e^{\beta t} dW\\
>&=-\beta \left( e^{-\beta t}\,X_{0} +  \sigma\,\int_{0}^{t}e^{-\beta (t-s)}\,dW(s)\right)dt + \sigma\,dW\\
>&= -\beta X_{t}\, dt +\sigma\,dW.
>\end{align*}
>$$


>[!important] Definition
>The solution $X_{t}$ of *Langevin equation* is called the **Ornstein–Uhlenbeck process**

- [[Ornstein–Uhlenbeck Process]]

## Explanation

>[!important]
>The Langevin equation can be thought as the **first-order linear differential equation** with additional *noise term*
>$$
> \frac{d}{dt} X_{t} =  -\beta X_{t} + \sigma \xi_{t}
>$$
>where $\xi_{t}$ is white noise.


>[!important]
>In discrete time, we have the **linear auto-regression**
>$$
>\begin{align*}
>X_{t+1} - X_{t} &= - \beta\,X_{t} + \sigma\,\xi_{t} \\
>X_{t+1} &= (1 - \beta)\,X_{t} + \sigma\,\xi_{t}
>\end{align*}
>$$
>where $\xi_{t} \sim \mathcal{N}(0,1)$ are i.i.d.

- [[Linear Regression]]

>[!important]
>The Langevin equation is a **linear stochastic differential equation** in narrow sense.

- [[Linear Stochastic Differential Equation]]
- [[Homogeneous Linear Stochastic Differential Equation]]


## Mean and Variance of the Solution

>[!important]
>The **mean function**
>$$
> \mathbb{E}\left[ X_{t} \right] = e^{-\beta\,t}\,\mathbb{E}\left[ X_{0} \right] 
>$$
>since the mean of stochastic integration with respect to Wiener process
>$$
> \mathbb{E}_{  }\left[ \int_{0}^{t}e^{-\beta (t-s)}\,dW(s) \right]  = 0
>$$

^2f9aa4

- [[Mean Function]]
- [[Ito Stochastic Integration]]
- [[Ito Isometry]]

>[!important]
>The **moment function**
>$$
> \mathbb{E}\left[ X_{t}^2 \right] = e^{-2 \beta t}\,\mathbb{E}\left[ X_{0}^2 \right] + \frac{\sigma^2}{2\beta}\left( 1 - e^{-2\beta t} \right) 
>$$

>[!important]
>The **variance function**
>$$
>\begin{align*}
> \text{Var}\left( X_{t} \right) &=  \mathbb{E}\left[ X_{t}^2 \right] - \left(  \mathbb{E}\left[ X_{t} \right]\right)^2 \\
> &= e^{-2 \beta t}\,\text{Var}(X_{0}) + \frac{\sigma^2}{2\beta}\left( 1 - e^{-2\beta t} \right)
>\end{align*}
>$$


>[!info]
>The **covariance function**
>$$
>\begin{align*}
>  &\mathbb{E}\left[ (X_{t} - \mu_{t})\,(X_{r} - \mu_{r}) \right] \\
> &= \mathbb{E}\left[ X_{t}X_{r}\right] -  \mu_{t}\mu_{r}\\
> &= \mathbb{E}\left[\left( e^{-\beta\,t}\,X_{0} + \sigma\,\int_{0}^{t}e^{-\beta (t-s)}\,dW(s) \right)  \left( e^{-\beta\,r}\,X_{0} + \sigma\,\int_{0}^{r}e^{-\beta (r-s)}\,dW(s) \right) \right] -  \mu_{t}\mu_{r}\\
>&=  e^{-\beta\,(t+r)} \mathbb{E}\left[ X_{0}^2 \right] -  \mu_{t}\mu_{r}\\
>&\quad + \sigma\,e^{-\beta\,t}\,\mathbb{E}\left[X_{0}\int_{0}^{r}e^{-\beta (r-s)}\,dW(s)\right] + \sigma\,e^{-\beta\,r}\,\mathbb{E}\left[X_{0}\int_{0}^{t}e^{-\beta (t-s)}\,dW(s)\right]\\
>&\quad + \sigma^2 \mathbb{E}\left[\int_{0}^{r}e^{-\beta (r-s)}\,dW(s) \int_{0}^{t}e^{-\beta (t-s)}\,dW(s)   \right]\\
>&= e^{-\beta\,(t+r)} \left( \mathbb{E}\left[ X_{0}^2 \right] - \left( \mathbb{E}\left[ X_{0} \right] \right)^2 \right)+ \sigma^2 \mathbb{E}\left[ \int_{0}^{r}e^{-\beta (r-s)}\,dW(s)  \int_{0}^{t}e^{-\beta (t-s)}\,dW(s) \right]\\
>&= e^{-\beta\,(t+r)}\text{Var}(X_{0}) + \sigma^2 e^{-\beta\,(t+r)} \mathbb{E}\left[\int_{0}^{\max\left\{ t,r \right\}}\mathbb{1}_{[0,r]}e^{\beta s}\,dW(s)\;\int_{0}^{\max\left\{ t,r \right\}}\mathbb{1}_{[0,t]}e^{\beta s}\,dW(s)   \right]\\
>&= e^{-\beta\,(t+r)}\text{Var}(X_{0}) + \sigma^2 e^{-\beta\,(t+r)} \mathbb{E}\left[ \int_{0}^{\max\left\{ t,r \right\}}\mathbb{1}_{[0,t]}\mathbb{1}_{[0,r]}e^{2\beta s}\,ds \right]\\
>&= e^{-\beta\,(t+r)}\text{Var}(X_{0}) + \sigma^2 e^{-\beta\,(t+r)}\mathbb{E}\left[ \int_{0}^{\min\left\{ t,r \right\}}e^{2\beta s}\,ds \right]\\
>&= e^{-\beta\,(t+r)}\text{Var}(X_{0}) + \sigma^2 e^{-\beta\,(t+r)}\frac{1}{2\beta}\left( -1 + e^{2\beta \min\{t, r\} } \right)\\
>&= e^{-\beta\,(t+r)}\text{Var}(X_{0}) + \sigma^2 \frac{ e^{-\beta\,|t - r|} - e^{-\beta\,(t+r)}}{2\beta}
>\end{align*}
>$$


>[!important]
>The **covariance function** of the solution (**Ornstein–Uhlenbeck process**) is 
>$$
>\begin{align*}
>K(t, r) = \text{Cov}(X_{t}, X_{r}) &= e^{-\beta\,(t+r)}\text{Var}(X_{0}) +  \frac{\sigma^2}{2\beta}\left[ e^{-\beta\,|t - r|} - e^{-\beta\,|t+r|} \right]\\
>&= e^{-\beta\,|t+s|}\left( \text{Var}(X_{0}) - \frac{\sigma^2}{2\beta} \right) + \frac{\sigma^2}{2\beta} e^{-\beta\,|t - s|}
>\end{align*}
>$$

^16825b

- [[Covariance Function of Gaussian Process]]


## Asymptotic Analysis

>[!important]
>As $t\to \infty$, we have
>$$
>\begin{align*}
>\mathbb{E}\left[ X_{t} \right] &= e^{-\beta\,t}\,\mathbb{E}\left[ X_{0} \right] &\to 0\\
>\text{Var}\left( X_{t} \right) &= e^{-2 \beta t}\,\text{Var}(X_{0}) + \frac{\sigma^2}{2\beta}\left( 1 - e^{-2\beta t} \right) &\to \frac{\sigma^2}{2\beta}
>\end{align*}
>$$
>
>This means that the solution of **Langevin equation** 
>$$
>\left\{
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= X_{0}
>\end{align*}
>\right.
>$$
>approaches to $$\mathcal{N}\left( 0,  \frac{\sigma^2}{2\beta}\right)$$ *irrespective to the initial distribution*.
>
>The **variance** of the **stationary distribution** reflect the *balance* between
>- the *random disturbance force* $(\sigma\,dW)$; and
>- the *frictional force* $(-\beta\,X_{t})$

^709c25


- [[Invariant Measure and Stationary Distribution]]
- [[Stationary Process]]



-----------
##  Recommended Notes and References


- [[Stochastic Differential Equations]]
- [[Stochastic Differential]]
- [[Ito Stochastic Integration]]
- [[Brownian Motion Wiener Process]]



- [[Gaussian Process]]
- [[Gauss–Markov Process]]
- [[Ornstein–Uhlenbeck Process]]


- [[Wasserstein Distance]]
- [[Wasserstein Space]]

- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 450 - 454