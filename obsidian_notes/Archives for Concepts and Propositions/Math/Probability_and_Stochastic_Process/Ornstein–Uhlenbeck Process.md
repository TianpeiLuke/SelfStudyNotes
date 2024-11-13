---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - ornstein–uhlenbeck_process
topics:
  - stochastic_process
name: Ornstein–Uhlenbeck Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Ornstein–Uhlenbeck Process

>[!important] Definition (1st Order ODE version.)
>The **Ornstein–Uhlenbeck process** $(X(t))$ is defined by the *first-order ordinary-differential equation* with *white noise model*
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} X(t) &= - \beta\, X(t) + \sigma\, \xi(t)\\
> X(0) &= X_{0}\\
>\end{align*}
>\right.
>$$
>where $\xi(\cdot)$ is the **Gaussian white noise**. 

- [[Langevin Equation]]

>[!important] Definition (2nd Order ODE version.)
>The **Ornstein–Uhlenbeck process** $(Y(t))$ can also be defined by the following *second-order ordinary-differential equation* with *white noise model*
>$$
>\left\{
>\begin{align*}
> \frac{d^2}{dt^2} Y(t) &= - \beta\, \frac{d}{dt} Y(t) + \sigma\, \xi(t)\\
> Y(0) &= Y_{0}\\
> \frac{d}{dt} Y(0) &= Y_{1}
>\end{align*}
>\right.
>$$
>where $\xi(\cdot)$ is the **Gaussian white noise**. 
>
>This process describes the **position** of *Brownian particles* under *frictional force*.

- [[Gauss–Markov Process]]
- [[White Noise Process]]
- [[Langevin Equation]]

### Formulation via Langevin Equation

>[!important]
>Define the *velocity process* $$X_{t} := \frac{d}{dt} Y(t),$$ we can convert the above second-order O.D.E. with white noise  into the **Langevin equation**
>$$
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= Y_{1}
>\end{align*}
>$$

- [[Langevin Equation]]
- [[Brownian Motion Wiener Process]]

## Explanation




## Ornstein-Uhlenbeck Process as Solution of Langevin Equation

>[!important] 
>The **Ornstein-Uhlenbeck process**  $X(t)$ as the solution of the *Langevin equation* is 
>$$
>X(t) = e^{-\beta t}\,Y_{1} + \sigma\,\int_{0}^{t}e^{-\beta (t-s)}\,dW(s)
>$$
>Note that for any $0 \le u < t$
>$$
>X(u) \perp \int_{u}^{t}e^{-\beta (t-s)}\,dW(s)
>$$
>This means that the **increment** of process is **independent** from the *past events*, i.e. the process is a **Markov process**. 

^6457d4

- [[Markov Chain and Markov Process]]

>[!important]
>Then the **position process** as the solution of the second-order O.D.E. can be found by
>$$
>Y(t) = Y_{0} + \int_{0}^{t}X(s)\,ds
>$$
>which is
>$$
>\begin{align*}
>Y(t) &= Y_{0} + \left(\int_{0}^{t} e^{-\beta s}\,ds \right)\,Y_{1} + \sigma\,\int_{0}^{t}e^{-\beta s}\, \int_{0}^{s}e^{ \beta u}\,dW(u)\,ds
>\end{align*}
>$$


## Mean and Variance

![[Langevin Equation#^2f9aa4]]

>[!important]
>The **mean function** of $Y_{t}$ can be computed as
>$$
>\begin{align*}
> \mathbb{E}\left[ Y(t) \right] &= \mathbb{E}\left[ Y_{0} \right] +  \mathbb{E}\left[  \int_{0}^{t}X(s)\,ds \right]\\
> &= \mathbb{E}\left[ Y_{0} \right] +    \int_{0}^{t}\mathbb{E}\left[X(s)\right]\,ds \\
> &=  \mathbb{E}\left[ Y_{0} \right] + \left( \int_{0}^{t}e^{-\beta s}ds \right) \mathbb{E}\left[ Y_{1} \right] \\
> &= \mathbb{E}\left[ Y_{0} \right] + \frac{1-e^{-\beta t}}{\beta} \mathbb{E}\left[ Y_{1} \right].
>\end{align*}
>$$

>[!important]
>The **variance function** of $Y_{t}$ can be computed as
>$$
>\begin{align*}
> \text{Var}\left( Y(t) \right)&= \text{Var}\left( Y_{0} \right) + \frac{\sigma^2}{\beta^2}t + \frac{\sigma^2}{2\beta^3}\left( -3 + 4\,e^{-\beta t} - e^{-2\beta t} \right).
>\end{align*}
>$$


## Covariance Function

![[Langevin Equation#^16825b]]


>[!important]
>Assume that $$\text{Var}(X_{0}) = \frac{\sigma^2}{2\beta} = 1,$$ and $\beta = 1.$ 
>
>The **covariance function** of *Ornstein–Uhlenbeck process* becomes
>$$
>K(s, t) = \exp \left(- \lvert\, t -s \,\rvert  \right).
>$$
>It is equivalent to the form
>$$
>K(s, t) = \exp \left(\frac{\min\{ s, t \}}{2}\right)\,\exp \left(-\frac{\max\{ s, t \}}{2}\right).
>$$
>That is, the **covariance function** is a **Laplacian kernel**. 

- [[Positive Definite Kernel Examples#Laplacian Kernel]]

>[!important]
>Under the above assumption, the *Ornstein–Uhlenbeck process* is an example of Gaussian process with **bounded variance**.


## Limit Distribution

![[Langevin Equation#^709c25]]


## Stationary Process

>[!important]
>When $$\text{Var}(X_{0}) = \frac{\sigma^2}{2\beta} = 1,$$ that  is, when  the power of the *friction* and *random perturbation* are equal,  the *Ornstein–Uhlenbeck process* is a **stationary process** since 
>$$
>K(s, t):= K(t - s) = \exp \left(- \beta\lvert\, t -s \,\rvert  \right).
>$$

- [[Stationary Process]]

>[!example]
>Note that a *stationary* **Ornstein–Uhlenbeck process** $X_{t}$ has *covariance function*  $$K(t, s) = \exp \left(-\beta\lvert t - s \rvert \right).$$
>
>We have the *spectral decomposition* of *covariance function*
>$$
>K(\tau) = \exp \left(-\beta |\tau|\right) = \int_{\mathbb{R}} \frac{2\beta}{\beta^2 + 4 \pi^2 \omega^2}\,e^{2\pi i \omega\,\tau}\,d\omega
>$$
>i.e. the **spectral density** is
>$$
>\rho(\omega) := \frac{2\beta}{\beta^2 + 4 \pi^2 \omega^2}.
>$$

- [[Fourier Series and Fourier Transform]]

>[!important]
>The **shift representation** of Ornstein–Uhlenbeck process is given by 
>$$
>X_{t} = \int_{t}^{\infty} \exp \left(- \frac{\beta (u-t)}{2}\right)\,d\mathcal{W}(u)
>$$


## Fokker–Planck–Kolmogorov Equation

>[!important] Theorem
>Let $(X_{t})$ be the **Ornstein-Uhlenbeck process** defined by the stochastic differential equation:
>$$
>\left\{
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= X_{0}
>\end{align*}
>\right.
>$$
>
>Let $p(x,t)$ be a *probability density function* which specifies the probability of finding the process $X(t)$ *in state* $x$ *at time* $t$.
>
>Then $p(x,t)$ satisfies the following **Fokker–Planck–Kolmogorov equation**
>$$
>\begin{align*}
>\frac{ \partial  }{ \partial t }p(x, t) &= \beta\,\frac{ \partial  }{ \partial x }\left( x\,p(x,t) \right) + \frac{\sigma^2}{2}\frac{ \partial^2 }{ \partial x^2 }p(x,t)
>\end{align*}
>$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]







-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]
- [[Gauss–Markov Process]]

- [[Langevin Equation]]

- [[Ito Stochastic Integration]]


- [[Wasserstein Distance]]
- [[Wasserstein Space]]

- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Lectures on Gaussian Processes by Lifshits]]
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 86
- Wikipedia [Ornstein-Uhlenbeck_process](https://en.wikipedia.org/wiki/Ornstein%E2%80%93Uhlenbeck_process)