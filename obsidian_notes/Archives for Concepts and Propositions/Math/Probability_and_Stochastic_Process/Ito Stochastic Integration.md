---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_integration
topics:
  - stochastic_process
name: Itô Stochastic Integration
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Stochastic Integration

![[Progressively Measurable Stochastic Process#^7e5649]]


>[!important] Proposition
>Let $(X_{t}, t\in [0,T]) \in \mathbb{L}^2([0,T])$ be *progressive measurable stochastic process* such that 
>$$
>\mathbb{E}_{\mathcal{P}}\left[  \int_{0}^{T}X^2_{t}dt \right] < \infty.
>$$
>
>Then there *exists* a sequence of **bounded step processes** $(X^n_{t}) \in \mathbb{L}^2(T)$ such that as $n\to \infty$, 
>$$
>\begin{align*}
>\mathbb{E}_{\mathcal{P}}\left[\left(\int_{0}^{T}\left(X_{t}^n  - X_{t} \right)dW\right)^2 \right]  &= \mathbb{E}_{\mathcal{P}}\left[  \int_{0}^{T} (X^n_{t} - X_{t})^2dt \right] \to 0.
>\end{align*}
>$$
>
>In other word, the **limit** $$\int_{0}^{T}X_{t}^n\,dW$$ **exists** *in* $L^2(\Omega, \mathcal{P})$ topology.

- [[Ito Stochastic Integration of Step Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

>[!important] Definition
>Let $(X_{t}, t\in [0,T]) \in \mathbb{L}^2([0,T])$ be *progressive measurable stochastic process* such that 
>$$
>\mathbb{E}_{\mathcal{P}}\left[  \int_{T}X^2_{t}dt \right] < \infty.
>$$
>
>The **Itô stochastic integral** of $(X_{t})$ on domain $[0,T]$ is defined as the limit of a sequence of integral of bounded step processes $(X_{t}^n) \in \mathbb{L}^2([0,T])$
>$$
>\int_{0}^T X_{t}\,dW := \lim_{ n \to \infty } \int_{0}^{T}X_{t}^n\,dW
>$$
>in $L^2(\Omega, \mathcal{P})$ topology.

^ad88e0

>[!important] Definition
>The **Itô indefinite stochastic integral** is defined as
>$$
>I(t) := \int_{0}^{t} X_{s}\,dW
>$$
>where $t\in [0,T]$.

^3fa129


## Expansion

>[!important] Definition
>Let $(X_{t}, t\in [0,T]) \in \mathbb{M}^2([0,T])$ be *progressive measurable stochastic process* such that 
>$$
>\int_{T}X^2_{t}dt < \infty, \quad \omega\text{-a.s.}
>$$
>
>The **Itô stochastic integral** of $(X_{t})$ on domain $[0,T]$ is defined as the limit of a sequence of integral of bounded step processes $(X_{t}^n) \in \mathbb{M}^2([0,T])$
>$$
>\int_{0}^T X_{t}\,dW := \lim_{ n \to \infty } \int_{0}^{T}X_{t}^n\,dW
>$$
>in $L^2(\Omega, \mathcal{P})$ topology.

- [[Progressively Measurable Stochastic Process]]

## Explanation

>[!important]
>The development of Itô stochastic integral follows the similar step in the development of **Lebesgue integral**.
>
>That is, it 
>- first construct simple integration on simple function (**step process** in this case),
>- then generalize it to *all integrable function* (**joint integrable** in this case)

- [[Development of Integrations]]
- [[Lebesgue-Stieltjes Integration]]


>[!important] 
>The **Itô stochastic integral** can be constructed using Riemann Sum
>$$
>\sum_{i=0}^{k_{n}-1}X(t_{i}^n)\left(W_{t_{i+1}^n} - W_{t_{i}^n}\right) \to \int_{0}^T X_{t}\,dW
>$$
>where $P^n = (t_{0}^n, \,{,}\ldots{,}\, t_{k_{n}-1}^n)$ is a **partition** on $[0,T]$, and $t_{0}^n =0$ and $t_{k_{n}-1}^n = T.$
>
>Compare to the traditional Riemann Sum definition in [[Riemann Integration]], we see that instead of choosing *arbitrary* **tagged partition** point $\tilde{t_{i}^{n}} \in [t_{i}^n, t_{i+1}^{n})$, in **Itô stochastic integral**, the tagged point is always the **left boundary point**:
>$$
>\tilde{t_{i}^{n}} = t_{i}^n.
>$$

- [[Riemann–Stieltjes Integration]]

## Properties

>[!important] Proposition
>Let $X, \;Y\in \mathbb{L}^2([0,T])$ be *progressive measurable processes*, and $a, b\in \mathbb{R}$
>- **Linearity**: $$\int_{0}^{T} \left(a\,X_{t} + b\,Y_{t}\right)\;dW  = a\,\int_{0}^{T} X_{t}\;dW + b\,\int_{0}^{T} Y_{t}\;dW$$
>- **Centered**: the expectation of *Itô stochastic Integration* is zero, i.e. $$\mathbb{E}\left[  \int_{0}^{T} X_{t}\;dW \right] = 0$$
>- **Itô Isometry**: 
>  $$
>  \mathbb{E}\left[ \left(\int_{0}^{T} X_{t}\;dW \right)^2 \right] = \mathbb{E}\left[  \int_{0}^{T} X^2_{t}\;dt \right]
> $$
> - **Itô Isometry for Product**
> $$
>  \mathbb{E}\left[ \int_{0}^{T} X_{t}\;dW\;\int_{0}^{T} Y_{t}\;dW \right] = \mathbb{E}\left[  \int_{0}^{T} X_{t}\,Y_{t}\;dt \right]
> $$

- [[Ito Isometry]]

## Integration by Parts

- [[Integration by Parts of Itô Stochastic Integration]]




-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Riemann–Stieltjes Integration]]
- [[Ito Stochastic Integration of Step Process]]


- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]