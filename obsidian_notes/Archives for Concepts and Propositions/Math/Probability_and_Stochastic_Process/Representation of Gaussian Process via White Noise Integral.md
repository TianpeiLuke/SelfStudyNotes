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
name: Gaussian Random Function via While Noise Integral
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: While Noise Integral Representation of Gaussian Random Function 

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space*. 
>
>For any *centered Gaussian process* $(X_{t}, t\in T)$, with *covariance function* $K: T\times T\to \mathbb{R}$ defined as 
>$$
>K(t, s) = \mathbb{E}\left[X_{t}\,X_{s} \right],
>$$
>we can find
>- a *measure space*  $(\mathcal{X}, \mathscr{A}, \mu)$ with $$\mathscr{A}_{0} := \left\{ A\in \mathscr{A}: \mu(A) < \infty \right\},$$
>- and **a white noise process** $(\mathcal{W}_{A}: A\in \mathscr{A}_{0})$  on  $(\mathcal{X}, \mathscr{A}, \mu)$  with **control measure** $\mu$
>- and a *family of functions* $\{ m_{t}, t\in T \}$ where $$m_{t} \in L^2(\mathcal{X}, \mathscr{A}, \mu)$$ such that for any $s,t\in T$, $$\int_{\mathcal{X}}\,m_{t}\,m_{s}\,d\mu = K(t, s).$$
>  
>In this case, the Gaussian process $(X_{t}, t\in T)$ has representation
>$$
>\begin{align*}
> X(\omega, t) = \int_{\mathcal{X}}\,m_{t}(u)\;d\mathcal{W}(\omega, u)
>\end{align*}
>$$ 
>or
>$$
>X_{t} = \int_{\mathcal{X}}\,m_{t}\,d\mathcal{W}.
>$$
>We call above expression as **the integral representation** of *Gaussian process*.

- [[Integration with respect to Wiener Measure]]
- [[Wiener Measure as Random Finitely Additive Measures]]
- [[Gaussian Process]]
- [[Covariance Function of Gaussian Process]]

## Examples


>[!example] 
>Let $(\mathbb{R}, \mathcal{L}[\mathbb{R}], m)$ be the **Lebesgue measure space**. Define a family of **indicator functions** $\{ m_{t}(\cdot), t\in \mathbb{R} \}$  as
>$$
>m_{t}(x) = \mathbb{1}\{ x \in (-\infty, t] \} \in L^2(\mathbb{R}, \mathcal{L}[\mathbb{R}], m)
>$$
>Then 
>$$
>W_{t} := \mathcal{W}((-\infty, t]) = \int_{\mathbb{R}} m_{t}\;d\mathcal{W}
>$$
>is a **Brownian Motion**.

- [[Integration with respect to Wiener Measure]]
- [[Brownian Motion Wiener Process]]

## Spectral Representation of Stationary Gaussian Process

- [[Spectral Representation of Stationary Process]]


-----------
##  Recommended Notes and References

- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]
- [[Gaussian Random Function]]

- [[Wiener Measure as Random Finitely Additive Measures]]
- [[Integration with respect to Wiener Measure]]

- [[Lectures on Gaussian Processes by Lifshits]]