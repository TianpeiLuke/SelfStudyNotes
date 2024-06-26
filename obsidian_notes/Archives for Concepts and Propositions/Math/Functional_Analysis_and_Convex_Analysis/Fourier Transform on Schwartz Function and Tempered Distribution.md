---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
keywords:
  - fourier_transform
  - function_rapid_decrease
  - tempered_distribution
topics:
  - functional_analysis
  - probability
name: Fourier Transform on Schwartz Function and Tempered Distribution
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Fourier Transform on Schwartz Function and Tempered Distribution

### Schwartz Function

>[!important] Definition (Schwartz Function)
>Let $\mathscr{S}(\mathbb{R}^d)$ be a space of **Schwartz functions** (functions with *rapid decrease*)
>
>The **Fourier transform** for $f\in \mathscr{S}(\mathbb{R}^d)$ is defined as 
>$$
>\begin{align*}
>(\mathcal{F}f)(\boldsymbol{\omega}) := \hat{f}(\boldsymbol{\omega}) = \int_{\mathbb{R}^d}f(\boldsymbol{t})\,e^{-i 2\pi \left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t} \right\rangle} d\boldsymbol{t}
>\end{align*}
>$$
>where  $$\left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t} \right\rangle = \sum_{i=1}^n\,\omega_{i}\,t_{i},$$  $\mathcal{F}: \mathscr{S}(\mathbb{R}^d) \to \mathscr{S}(\mathbb{R}^d)$ is a *linear operator.* That is $\mathcal{F}\in \mathcal{L}(\mathscr{S}(\mathbb{R}^d)).$


- [[Space of Functions of Rapid Decrease and Schwartz Class]]

>[!important] Definition (Schwartz Function)
>Let $\mathscr{S}(\mathbb{R}^d)$ be a space of **Schwartz functions** (functions with *rapid decrease*)
>
>Define the **flip operator** $\mathcal{R}: \mathscr{S}(\mathbb{R}^d) \to \mathscr{S}(\mathbb{R}^d)$ as 
>$$
>(\mathcal{R}f)(x) := f(-x) 
>$$
>
>The **inverse Fourier transform** of $f\in \mathscr{S}(\mathbb{R}^d)$ is defined as
>$$
>f^{\lor}(\boldsymbol{t}) := (\mathcal{F}^{-1}f)(\boldsymbol{t}) = \mathcal{F}(\mathcal{R}f)(\boldsymbol{t}) = \int_{\mathbb{R}^d}f(\boldsymbol{\omega})\,e^{i 2\pi \left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t}  \right\rangle} d\boldsymbol{\omega}
>$$
>Thus the inverse Fourier transform is
>$$
>\mathcal{F}^{-1} = \mathcal{F}\,\mathcal{R} = \mathcal{R}\,\mathcal{F}.
>$$


>[!important] Theorem
>The **Fourier transform** $\mathcal{F}: \mathscr{S}(\mathbb{R}^d) \to \mathscr{S}(\mathbb{R}^d)$ is a **homeomorphism** from $\mathscr{S}(\mathbb{R}^d)$ onto itself.
>
>That is $$f(t) \stackrel{\mathcal{F}}{\rightarrow} \hat{f}(\omega), \quad \hat{f}(\omega) \stackrel{\mathcal{F}^{-1}}{\rightarrow} f(t)$$

- [[Homeomorphism]]

### Tempered Distribution

>[!important]
>We can define the *Fourier transform*  $\mathcal{F}: \mathscr{S}'(\mathbb{R}^d) \to \mathscr{S}'(\mathbb{R}^d)$ on **the space of tempered distributions**.
>
>Specifically, for $f\in \mathscr{S}'(\mathbb{R}^d)$, we define $\mathcal{F}f$ via integral equation
>$$
>\left\langle  \mathcal{F}f\,,\,\phi \right\rangle := \left\langle  f\,,\,\mathcal{F}\phi    \right\rangle
>$$
>for all *Schwartz function* $\phi \in \mathscr{S}(\mathbb{R}^d).$ 
>
>Here $\mathcal{F}\phi$ is defined the same way as above
>$$
>(\mathcal{F}\phi)(\boldsymbol{\omega}) := \int_{\mathbb{R}^d}f(\boldsymbol{t})\,e^{-i 2\pi \left\langle  \boldsymbol{\omega}\,,\,\boldsymbol{t} \right\rangle} d\boldsymbol{t}
>$$

- [[Space of Tempered Distributions]]


## Explanation

>[!important]
>The pair
>$$
>f(t) \stackrel{\mathcal{F}}{\rightarrow} \hat{f}(\omega)
>$$
>is called the **Fourier pair**.

## Inverse Fourier Transform





-----------
##  Recommended Notes and References

- [[Fourier Series and Fourier Transform]]

- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Space of Tempered Distributions]]
- [[Fréchet Space]]



- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]


- Wikipedia [Fourier_transform](https://en.wikipedia.org/wiki/Fourier_transform)