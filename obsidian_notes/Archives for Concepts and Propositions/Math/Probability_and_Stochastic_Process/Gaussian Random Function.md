---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - gaussian_function
topics:
  - probability
  - stochastic_process
name: Gaussian Random Function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Gaussian Random Function in Topological Vector Space

>[!important] Definition
>Let $\mathcal{X}$ be a real *topological vector space*, and $\mathcal{X}^{*}$ be the *dual space* of $\mathcal{X}$.  $\left\langle \cdot , \cdot \right\rangle: \mathcal{X}^{*} \times \mathcal{X} \to \mathbb{R}$ defines *the canonical dual pairing*. 
>
>A **random element** $X \in \mathcal{X}$ is called **Gaussian**, if 
>$$
> \begin{align*}
> \left\langle f , X \right\rangle := f(X) \sim \mathcal{N}(\mu, \sigma^2)
> \end{align*}  
>$$ 
>is a *Normal random variable*, for **all  $f \in \mathcal{X}^{*}$**.

- [[Random Element and Random Variable]]
- [[Canonical Dual Pairing]]
- [[Topological Vector Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Gaussian Measure]]


## Explanation


>[!important] Proposition
>Let $(\mathcal{X}, \mathscr{F}, \mathcal{P})$ be a probability space, where  $\mathcal{X}$ is a *locally convex topological vector space* and $\mathcal{P}$ is a *Radon measure.* 
>
>*Every* **Gaussian random element** $X$ in $\mathcal{X}$ possesses an **expectation** and a **covariance operator**. 
>
>In other word, $X \sim \mathcal{N}(a, K)$, where $a\in \mathcal{X}$ is the expectation of $X$ and $K: \mathcal{X}^{*} \to \mathcal{X}$ is the covariance operator.

- [[Locally Convex Space]]
- [[Mean Function]]
- [[Covariance Operator]]



>[!info]
> - The above proposition holds if $\mathcal{X}$ is *metrizable*, *complete*, *locally convex* topological vector space.
> - It also holds if $\mathcal{X}$ is a *separable Banach space*.

- [[Banach Space]]
- [[Second Countablity]]
- [[Complete Topological Vector Space]]
- [[Probability Space]]
- [[Radon Measure]]

## Gaussian Function on Hilbert Space

- [[Representation of Gaussian Random Function in Hilbert Space]]

## Concentration of Gaussian Measure on Infinite Dimensional Space

- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]








-----------
##  Recommended Notes and References

- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]