---
tags:
  - concept
  - math/probability
  - math/functional_analysis
keywords:
  - characteristic_function_random_variable
topics:
  - probability
name: Characteristic Function of Random Variable
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: Characteristic Function of Random Variable

>[!important] Definition
>The **characteristic function** of a *random variable* $X: \Omega \to \mathbb{R}$ is defined by
>$$
>\begin{align*}
>\phi_{X}(t) &:=  \mathbb{E}_{ \mathcal{P} }\left[ e^{itX} \right], \quad t\in \mathbb{R}.\\
>&= \int_{\Omega}e^{itX}d\mathcal{P}\\
>&= \int_{\mathbb{R}}e^{itx} dF_{X}(x)
>\end{align*}
>$$
>where $F_{X}(\lambda)$ is the **cumulative distribution function**.


- [[Expectation of Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]

>[!important] Definition
>- If $X: \Omega \to \mathbb{R}^{d}$,  for any $t\in \mathbb{R}^d$, we have $$\phi_{X}(t)= \mathbb{E}_{ \mathcal{P} }\left[ \exp\left(i \, t^T\,X \right) \right]$$
>- If $X: \Omega \to \mathbb{R}^{k \times d}$,  for any $t\in \mathbb{R}^{k\times d}$,  $$\phi_{X}(t)= \mathbb{E}_{ \mathcal{P} }\left[  \exp\left(i \,\text{tr}\left(t^T\,X\right)\right) \right]$$
>- If $X: \Omega \to \mathbb{C}^{d}$,  for any $t\in \mathbb{C}^d$, $$\phi_{X}(t)= \mathbb{E}_{ \mathcal{P} }\left[  \exp\left(i \,\mathrm{Re}\left(t^H\,X\right) \right) \right]$$


## Explanation

>[!info]
>The characteristic function of random variable $X$ can be seen as the  **Fourier transform** of the **p.d.f.** of $X$ when $-\omega$ is used
>$$
>\phi_{X}(\omega) = \int_{\Omega}e^{i\omega x}\,p_{X}(x)\,dx = (\mathcal{F}\;p_{X})(-\omega)
>$$

- [[Fourier Series and Fourier Transform]]
- [[Probability Density Function of Random Variable]]

## Relation to Moment Generating Functions

>[!important]
>The **characteristic function** can be derived from the **moment generating function**
>$$
>\phi_{X}(t) = M_{X}(it) \iff M_{X}(t) = \phi_{X}(-it)
>$$

- [[Moment Generating Function]]

## Convergence in Distribution

- [[Continuity Theorem for Convergence in Distribution]]



-----------
##  Recommended Notes and References


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]

- [[Real Analysis Modern Techniques and Their Applications by Folland]]