---
tags:
  - concept
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - haar_wavelet_function
topics:
  - functional_analysis
  - stochastic_process
name: Haar Wavelet Function
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Haar Wavelet Function

>[!important] Definition
>The family $\{ h_{k} \}$ of functions is called **Haar wavelet functions** on $[0,1]$ if we define
>- for $k=0$, $h_{0}(t) = 1$ for $t\in [0,1]$ and
>- for $k=1$,
>$$
>h_{1}(t) = \left\{
>\begin{array}{cc}
>1& t\in \left[0,  \frac{1}{2} \right] \\ 
>-1 & t\in \left[ \frac{1}{2},  1 \right]
>\end{array}\right.
>$$
>- for any $$k \in \left[ 2^n, 2^{n+1} \right), n \ge 1 \in \mathbb{N},$$ we define 
>$$
>h_{k}(t) = \left\{
>\begin{array}{cc}
>2^{n / 2} & t\in \left[ \frac{k - 2^n}{2^n},  \frac{k - 2^n + 1 / 2}{2^n} \right] \\ 
>-2^{n / 2} & t\in \left[ \frac{k - 2^n + 1 / 2}{2^n},  \frac{k - 2^n + 1}{2^n} \right] \\ 
> 0 & \text{ otherwise}
>\end{array}\right.
>$$
> 

^e6b662


### Mother Function and Scaling Function

>[!important]
>The **mother function** of Haar wavelet is 
>$$
>\psi(x) := \left\{
>\begin{array}{cc}
>1 & x \in \left[0,  \frac{1}{2}\right)\\ 
>-1 & x \in \left[\frac{1}{2}, 1\right) \\ 
>0 & \text{otherwise}
>\end{array}\right.
>$$

>[!important]
>The **scaling function** of Haar wavelet is 
>$$
>\varphi(x) := \left\{
>\begin{array}{cc}
>1 & x \in \left[0,  1\right)\\ 
>0 & \text{otherwise}
>\end{array}\right.
>$$

>[!important] Definition
>For each $n, k\in \mathbb{N}$, the **Haar wavelet** $\psi_{n,k}: \mathbb{R} \to \mathbb{R}$ is defined as 
>$$
>\psi_{n,k}(x) := 2^{n / 2}\psi\left(2^n\,x - k\right)
>$$


## Explanation


## Complete Orthonormal Basis

>[!important]
>$$
>\begin{align*}
>\int_{\mathbb{R}}\psi_{n,k}(x) dx &= 0 \\
>\lVert \psi_{n,k} \rVert_{L^2}^2 &:= \int_{\mathbb{R}}\psi_{n,k}^2(x) dx = 1 \\
> \int_{\mathbb{R}}\psi_{n,k}(x)\,\psi_{m, j} dx &= \delta_{n, m}\,\delta_{k, j} 
>\end{align*}
>$$


>[!important] Theorem
>The family $$\{ \psi_{n,k}, \;n\in \mathbb{N}, k\in \mathbb{N} \}$$  of **Haar wavelets** forms a **complete orthonormal basis** in $L^2[0,1]$.

- [[Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Lp Space]]


## Approximation

>[!important] Proposition
>Any **continuous** real function with **compact support** can be *approximated* **uniformly** by linear combinations of $$\{ \varphi(2^n\,x), n=0, 1 \,{,}\ldots{,}\, \}$$

>[!important] Proposition
>The **mother function** $\psi$ and **scaling function** $\varphi$ of **Haar wavelet** can be obtained *recursively* by
>$$
>\begin{align*}
>\varphi(x) &= \varphi(2x) + \varphi(2x - 1)\\
>\psi(x) &= \varphi(2x) - \varphi(2x - 1)
>\end{align*}
>$$ 

## Schauder Function

- [[Schauder Function]]



-----------
##  Recommended Notes and References


- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Dyadic Algebra]]




- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Introduction to Measure Theory by Tao]]

- [[Introduction to Stochastic Differential Equations by Evans]]

- Wikipedia [Haar wavelet](https://en.wikipedia.org/wiki/Haar_wavelet)