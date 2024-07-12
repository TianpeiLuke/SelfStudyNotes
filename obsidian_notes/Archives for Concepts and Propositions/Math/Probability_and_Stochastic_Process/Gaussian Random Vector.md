---
tags:
  - concept
  - math/probability
keywords:
  - gaussian_vector
  - gaussian_measure
topics:
  - probability
name: Gaussian Random Vector
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Gaussian Random Vector

>[!important] Definition
>A **random vector** $X \in \mathbb{R}^n$ is called **Gaussian**, if 
>$$
>\left\langle \nu , X \right\rangle \sim \mathcal{N}(\mu, \sigma^2)
>$$
>Normal random variable for **each** $v \in \mathbb{R}^n$.

- [[Random Element and Random Variable]]

>[!important]
>The **joint distribution** of *Gaussian random vector* $X \in \mathbb{R}^n$ is
>$$
>\mathcal{N}(x; \mu, \Sigma) = \frac{1}{\sqrt{(2\pi)^{n}|\det(\Sigma)| }}\exp \left(-\frac{1}{2}\left(x - \mu\right)^T\,\Sigma^{-1}\,(x - \mu)\right)
>$$
>where $\mu \in \mathbb{R}^n$ and $\Sigma \succ 0$.

- [[Positive Semidefinite Transformation]]

## Explanation



-----------
##  Recommended Notes and References

- [[Gaussian Random Variable]]
- [[Gaussian Measure]]
- Wikipedia [Multivariate_normal_distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)