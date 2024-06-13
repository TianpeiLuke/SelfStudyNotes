---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - gaussian_function
  - karhunen_loeve_expansion
topics:
  - probability
  - stochastic_process
name: Spectral Representation of Stationary Process
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Spectral Representation of Stationary Process


>[!important]
>Let $(X_{t}, t\in T)$ be a **wide-sense stationary (WSS) Gaussian process** with covariance function $$\mathbb{E}\left[  X_{t}\,X_{s} \right] := K(t - s).$$
>
>By **spectrum theorem**, the symmetric positive semi-definite map $K: \mathbb{R} \to \mathbb{R}$ has *spectral decomposition* (i.e. *Fourier transform*)
>$$
>K(\tau) = \int_{-\infty}^{\infty} \exp \left(i \pi\,\tau\,u\right)\,d\mu(u).
>$$
>where $\mu$ is the *spectral measure* on $\mathbb{R}$.
>
>We can show that $X_{t}$ has **spectral representation**
>$$
>\begin{align*}
>X(\cdot, t) =  \int_{-\infty}^{\infty} \exp \left(i\pi\,t\,u\right)\,d\mathcal{W}(\cdot, u),
>\end{align*}
>$$
>where $(\mathcal{W}_{A})$ is *complex-valued Gaussian white noise*.

- [[Representation of Gaussian Process via White Noise Integral]]
- [[Stationary Process]]
- [[Covariance Function of Gaussian Process]]
- [[Positive Semidefinite Operator]]
- [[Fourier Series and Fourier Transform]]

## Explanation




## Examples


>[!example]
>Note that a **Ornstein–Uhlenbeck process** $X_{t}$ is a stationary process whose *covariance function* is $$K(t, s) = \exp \left(-\lvert t - s \rvert \right).$$
>
>We have the *spectral decomposition* of *covariance function*
>$$
>K(\tau) = \exp \left(-|\tau|\right) = \int_{\mathbb{R}} \frac{2\exp \left(i u\,\tau\right)}{\pi (1 + 4 u^2)}\,du
>$$
>i.e. the **spectral density** is
>$$
>\rho(u) := \frac{2}{\pi (1 + 4 u^2)}.
>$$
>
>The **shift representation** of Ornstein–Uhlenbeck process is given by 
>$$
>X_{t} = \int_{t}^{\infty} \exp \left(- \frac{(u-t)}{2}\right)\,d\mathcal{W}(u)
>$$


- [[Ornstein–Uhlenbeck Process]]


-----------
##  Recommended Notes and References

- [[Wiener Measure as Random Finitely Additive Measures]]
- [[Representation of Gaussian Process via White Noise Integral]]

- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]
- [[Gaussian Random Function]]

- [[Wiener Measure as Random Finitely Additive Measures]]
- [[Integration with respect to Wiener Measure]]

- [[Lectures on Gaussian Processes by Lifshits]]