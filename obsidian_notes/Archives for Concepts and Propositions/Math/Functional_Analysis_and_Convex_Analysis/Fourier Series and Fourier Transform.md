---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
  - electrical_engineering/signal_processing
keywords:
  - fourier_transform
  - fourier_series
topics:
  - functional_analysis
  - probability
name: Fourier Series and Fourier Transform
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Fourier Series and Fourier Transform


>[!important] Definition (on $\mathbb{R}$)
>Let $(\mathbb{R}, \mathscr{B}, m)$ be a *Lebesgue measure space* and $f\in L^1(\mathbb{R})$ be an *absolutely integrable function*.
>
>The **Fourier transform** for $f\in L^1(\mathbb{R})$ is defined by
>$$
>\begin{align*}
>(\mathcal{F}f)(\omega) := \hat{f}(\omega) = \frac{1}{\sqrt{ 2\pi }}\int_{-\infty}^{+\infty}f(t)\,e^{-i 2\pi \omega t} dt
>\end{align*}
>$$
>where  $\mathcal{F}: L^1(\mathbb{R}) \to L^1(\mathbb{R})$ is a *linear operator.* That is $\mathcal{F}\in \mathcal{L}(L^1(\mathbb{R})).$
>

^677ad7


- [[Absolutely Convergent Integration]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Space of Bounded Linear Operators]]
- [[Lp Space]]

>[!important] Definition (on $\mathbb{R}^d$)
>Let $(\mathbb{R}^d, \mathscr{B}, m)$ be a *Lebesgue measure space* and $f\in L^1(\mathbb{R}^d)$ be an *absolutely integrable function*.
>
>The **Fourier transform** for $f\in L^1(\mathbb{R}^d)$ is defined as 
>$$
>\begin{align*}
>(\mathcal{F}f)(\boldsymbol{\omega}) := \hat{f}(\boldsymbol{\omega}) = \frac{1}{(2\pi)^{d / 2} }\int_{\mathbb{R}^d}f(\boldsymbol{t})\,e^{-i 2\pi \left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t} \right\rangle} d\boldsymbol{t}
>\end{align*}
>$$
>where  $\mathcal{F}: L^1(\mathbb{R}^d) \to L^1(\mathbb{R}^d)$ is a *linear operator.* That is $\mathcal{F}\in \mathcal{L}(L^1(\mathbb{R}^d)).$


>[!important]
>- The domain of function $f\in L^1(\mathbb{R})$ is often called the **time domain**. Denote the time domain variable as the **time** $t$
>- The domain of function $\mathcal{F}(f) \in L^1(\mathbb{R})$ is often called the **frequency domain**. Denote the frequency domain variable as the frequency $\omega$.


## Inverse Fourier Transform

>[!important] Definition (on $\mathbb{R}^d$)
>Let $(\mathbb{R}^d, \mathscr{B}, m)$ be a *Lebesgue measure space* and $f\in L^1(\mathbb{R}^d)$ be an *absolutely integrable function*.
>
>The **inverse Fourier transform** for $f\in L^1(\mathbb{R}^d)$ is defined as 
>$$
>\begin{align*}
>(\mathcal{F}^{-1}f)(\boldsymbol{t}) = f^{\lor}(\boldsymbol{t}) &= \frac{1}{(2\pi)^{d / 2} }\int_{\mathbb{R}^d}f(\boldsymbol{\omega})\,e^{i 2\pi \left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t} \right\rangle} d\boldsymbol{\omega}
>\end{align*}
>$$
>

^3a1551


## Explanation

>[!important]
>The pair
>$$
>f(t) \stackrel{\mathcal{F}}{\rightarrow} \hat{f}(\omega)
>$$
>is called the **Fourier pair**.


>[!important] Theorem
>The **Fourier transform** $\mathcal{F}: L^1(\mathbb{R}^d) \to  L^1(\mathbb{R}^d)$ is a **homeomorphism** from $L^1(\mathbb{R}^d)$ onto itself (i.e. an **automorphism**).
>
>That is $$f(t) \stackrel{\mathcal{F}}{\rightarrow} \hat{f}(\omega), \quad \hat{f}(\omega) \stackrel{\mathcal{F}^{-1}}{\rightarrow} f(t)$$

- [[Homeomorphism]]
- [[Automorphism between Groups]]

### Compare to Taylor Series

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]


## Fourier Inversion Theorem

>[!important]
>On $L^1(\mathbb{R}^d)$, the **Fourier transform** and the **inverse Fourier transform** both *exists*.
>
>Moreover, both $$\mathcal{F}^{-1}(\mathcal{F}f) =f$$ and $$\mathcal{F}(\mathcal{F}^{-1}g) =g.$$ hold *pointwise almost everywhere*.


## Properties




## Generalization 

- [[Fourier Transform on Schwartz Function and Tempered Distribution]]

## Spectral Decomposition of Fourier Transform

- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Hermite Polynomials]]


## Discrete Fourier Transform


- [[Discrete Fourier Transform]]
- [[Fast Fourier Transform]]


-----------
##  Recommended Notes and References

- [[Hilbert Space]]
- [[Fourier Basis Function]]
- [[Discrete Fourier Transform]]
- [[Fast Fourier Transform]]

- [[Characteristic Function of Random Variable]]

- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]

- [[Signals and Systems by Oppenheim]]
- [[Discrete Time Signal Processing by Oppenheim]]

- Wikipedia [Fourier_transform](https://en.wikipedia.org/wiki/Fourier_transform)