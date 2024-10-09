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

^a97326

- [[Positive Semidefinite Transformation]]

## Explanation

>[!info]
>The log-likelihood function for moment parameters is
>$$
>\log \mathcal{N}(x; \mu, \Sigma) = -\frac{n}{2} \log (2\pi) -\frac{1}{2} \log \det(\Sigma)   -\frac{1}{2}\left(x - \mu\right)^T\,\Sigma^{-1}\,(x - \mu)
>$$


## Exponential Family

>[!important] Definition
>The **multivariate Gaussian distribution** can be reparameterized according to the **canonical form** of an *exponential family* with  *canonical parameters* $\left( -\frac{1}{2}\Theta, \theta \right)$. That is,
>$$
>\begin{align*}
>p(x; \Theta, \theta) &= \exp \left( -\frac{1}{2} \left\langle \Theta x , x \right\rangle + \left\langle \theta, x \right\rangle - A(\theta, \Theta) \right) \\[5pt]
>&= \exp \left( \left\langle -\frac{1}{2} \Theta , x x^{T} \right\rangle_{tr} + \left\langle \theta, x \right\rangle - A(\theta, \Theta) \right)
>\end{align*}
>$$
>where $\Theta = \Sigma^{-1}$ is the **precision matrix** and the *inner product* between two matrix is defined as  
>$$
>\left\langle  A\,,\,B    \right\rangle_{tr} = \text{tr}\left(A^{T}\,B\right)
>$$
>- The bijective map between the **canonical parameters** $(\theta, \Theta)$ and $(\mu, \Sigma)$ is defined as
>$$
>\begin{align*}
> \Theta &= \Sigma^{-1}\\
> \theta &= \Sigma^{-1}\,\mu
>\end{align*}
>$$ 
>or 
>$$
>\begin{align*}
> \Sigma &= \Theta^{-1}\\
> \mu &= \Theta^{-1}\,\theta.
>\end{align*}
>$$ 
>- The **log-partition function**
>$$
>\begin{align*}
>A(\theta, \Theta) &= \frac{1}{2}\left[\left\langle \Theta^{-1}\theta , \theta \right\rangle - \log\det(\Theta) +  n \log \left( 2\pi\right) \right]\\[10pt]
>&= \frac{1}{2}\left(\left\langle \Sigma^{-1}\mu , \mu \right\rangle + \log\det(\Sigma) +  n \log \left( 2\pi\right) \right).
>\end{align*}
>$$


- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]



-----------
##  Recommended Notes and References


- [[Inverse Covariance Estimation]]

- [[Gaussian Random Variable]]
- [[Gaussian Measure]]
- Wikipedia [Multivariate_normal_distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] 
- [[Matrix CookBook by Petersen]] pp 40