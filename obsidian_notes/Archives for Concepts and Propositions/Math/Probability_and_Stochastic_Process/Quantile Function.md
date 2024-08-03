---
tags:
  - concept
  - math/probability
  - statistics/concentration_inequality
  - math/stochastic_process
keywords:
  - gaussian_quantile_function
  - quantile_function
  - generalized_inverse
topics:
  - probability
  - concentration_inequality
name: Quantile Function
date of note: 2024-08-02
---

## Concept Definition

>[!important]
>**Name**: Quantile Function

>[!important] Definition
>A **quantile function** $$Q: [0,1] \to \mathbb{R}$$ with respect to a  *cumulative distribution function* $F_{X}: \mathbb{R} \to [0,1]$ of a random variable $X$  is defined as the *generalized inverse* of $F_{X}$:
>$$
>Q(p) = \inf\left\{ x\in \mathbb{R}: F(x) \ge p \right\}
>$$

^700c00

- [[Cumulative Distribution Function of Random Variable]]


## Property

>[!important] Proposition
>The quantile is the **unique function** that satisfies the **Galois inequality**
>$$
>Q(p) \le x  \quad \iff \quad p \le F(x)
>$$
>If $F$ is **continuous** and **strictly monotonic increasing**, then the inequality is replaced by the inequality and we have 
>$$
>Q = F^{-1}
>$$
>
>In general, *without* assuming that $F$ has right or left inverse, we have $$Q\left( F(X) \right) = X\quad \text{ a.s.}$$




## Explanation

>[!important]
>A quantile function is the key for **Monte Carlo simulation**
>$$
>Q(U) \sim F \quad \text{ if }  U \sim \text{Uniform}[0,1]
>$$

- [[Fundamental Theorem of Simulation]]


## Ordinary Differential Equation

>[!important]
>The quantile function $Q(p)$ can be described by an **nonlinear ordinary differential equation**
>$$
> \frac{d^2}{dp^2} Q =  H(Q)\,\left( \frac{d}{dp}Q  \right)^2
>$$
>where 
>$$
>H(x) = - \frac{d}{dx} \log p(x) = - \frac{1}{p(x)} \frac{d}{dx} p(x) 
>$$
>and $p$ is the *probability density function* of random variable $X$

- [[Probability Density Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Ordinary Differential Equations]]

## Normal Quantile

- [[Gaussian Quantile Function or Probit Function]]




-----------
##  Recommended Notes and References



- [[Gaussian Quantile Function or Probit Function]]

- [[Cumulative Distribution Function of Random Variable]]
- [[Random Element and Random Variable]]

- [[Probability Space]]

- [[Monte Carlo and Applications]]

- [[Monte Carlo Statistical Methods by Robert]]
- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]
- Wikipedia [Quantile_function](https://en.wikipedia.org/wiki/Quantile_function)