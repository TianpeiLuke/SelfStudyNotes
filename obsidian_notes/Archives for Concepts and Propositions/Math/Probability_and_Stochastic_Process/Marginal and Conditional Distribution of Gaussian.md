---
tags:
  - concept
  - math/probability
  - probabilistic_graphical_models/theory
keywords:
  - marginal_distribution
  - conditional_probability
  - gaussian_variable
topics:
  - probability
  - probabilistic_graphical_model
name: Marginal and Conditional Distribution of Gaussian
date of note: 2024-07-25
---

## Concept Definition

>[!important]
>**Name**: Marginal and Conditional Distribution of Gaussian

### Marginal Distribution

>[!important] Proposition
>Let $(X, Y)$ be *joint normal distribution* defind as 
>$$
>p(x, y) = \mathcal{N}\left( (x,y);\; \mu,\, \Sigma \right)
>$$
>where
>$$
>\begin{align*}
> \Sigma &= \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right] \\[5pt]
> \mu&= \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right].
>\end{align*}
>$$
>
>Then the **marginal p.d.f.** over $Y$ is from the **normal distribution**
>$$
>p(y) = \int_{x \in \mathbb{R}}p(x, y)dx = \mathcal{N}(y\,;\, \mu_{y},\, \Sigma_{y y}).
>$$

- [[Partition of Matrix and Block Matrix]]
- [[Probability Density Function of Random Variable]]

### Conditional Distribution

>[!important] Proposition
>Let $(X, Y)$ be *joint normal distribution* defind as 
>$$
>p(x, y) = \mathcal{N}\left( (x,y);\; \mu,\, \Sigma \right)
>$$
>where
>$$
>\begin{align*}
> \Sigma &= \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right] \\[5pt]
> \mu&= \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right].
>\end{align*}
>$$
>Assume that $\Sigma_{x x} \succ 0$.
>
>Then the **conditional p.d.f.** of $Y$ given $X$ is from a **normal distribution**
>$$
>p(y \,|\, x) = \mathcal{N}(y\,;\, \mu_{y|x},\, \Sigma_{y|x}).
>$$
>where
>$$
>\begin{align*}
> \mu_{y|x} &= \mu_{y} + \Sigma_{y x}\,\Sigma_{x x}^{-1}\left(x - \mu_{x}\right) \\[5pt]
> \Sigma_{y|x} &= \Sigma_{y y} - \Sigma_{y x}\,\Sigma_{x x}^{-1}\,\Sigma_{x y} = \Sigma / \Sigma_{x x}
>\end{align*}
>$$
>Note that the *covariance* of the conditional distribution $\mathcal{P}(Y|X)$ is the **schur complement** of the *covariance matrix* of $X$ $$\Sigma / \Sigma_{x x} := \Sigma_{y y} - \Sigma_{y x}\,\Sigma_{x x}^{-1}\,\Sigma_{x y}.$$

^70f047


- [[Conditional Probability]]
- [[Probability Density Function of Random Variable]]
- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Kalman Filter Discrete-Time]]
- [[Normal Equations and Newton System of Equations]]

## Canonical Parameterization 

>[!important] 
>Let $(X, Y)$ be *joint normal distribution* defind as 
>$$
>p(x, y) = \mathcal{N}\left( (x,y);\; \mu,\, \Sigma \right) = p((x,y); \theta, \Theta)
>$$
>where the precision matrix $\Theta = \Sigma^{-1}$ and $\theta = \Sigma^{-1}\mu$. Here $\left( \theta, -\frac{1}{2}\Theta \right)$ forms the **canoincal parameter** of exponential family.
>
>Denote the block partition of covariance matrix
>$$
>\begin{align*}
> \Sigma &= \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right] \succ 0 \\[5pt]
> \mu&= \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right].
>\end{align*}
>$$
>We can derive the mapping between $(\Sigma, \mu)$ and $(\Theta, h)$
>$$
>\begin{align*}
> \Theta &= \left[\begin{array}{cc}
>\Theta_{x x} & \Theta_{x y} \\
>\Theta_{y x} & \Theta_{y y}
>\end{array}\right] = \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right]^{-1} \\[10pt]
>\theta &= \left[\begin{array}{c}
>\theta_{x}  \\
>\theta_{y} 
>\end{array}\right]  = \left[\begin{array}{cc}
>\Theta_{x x} & \Theta_{x y} \\
>\Theta_{y x} & \Theta_{y y}
>\end{array}\right] \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right] =  \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right]^{-1}\,\left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right] 
>\end{align*}
>$$
>Thus by **Schur complement**, and **Matrix Inversion Formula**, we have
>$$
>\begin{align*}
>\Theta_{y y} &= \left(\Sigma / \Sigma_{x x}\right)^{-1} =  \left(\Sigma_{y y} - \Sigma_{y x}\,\Sigma_{x x}^{-1}\,\Sigma_{x y} \right)^{-1} = \Sigma_{y|x}^{-1} \\[5pt]
> \Sigma_{y y} &= \left(\Theta / \Theta_{x x}\right)^{-1} = \left(\Theta_{y y} - \Theta_{y x}\,\Theta_{x x}^{-1}\,\Theta_{x y} \right)^{-1} \\[5pt]
> \Theta_{y x}&= -\left(\Sigma / \Sigma_{x x}\right)^{-1}\,\Sigma_{y x}\,\Sigma_{x x}^{-1}  \\[5pt]
> \iff \;\; \Theta_{y y}^{-1}\Theta_{y x} &= -\Sigma_{y x}\Sigma_{x x}^{-1} \\[5pt]
> \theta_{y} &= \Theta_{y y}\mu_{y} + \Theta_{y x}\mu_{x}  \\
> &= \left(\Sigma / \Sigma_{x x}\right)^{-1}\mu_{y} - \left(\Sigma / \Sigma_{x x}\right)^{-1}\,\Sigma_{y x}\,\Sigma_{x x}^{-1}\mu_{x}
>\end{align*}
>$$

^4a335a

- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [[Exponential Family of Distributions]]


>[!important] Proposition
>The **marginal p.d.f.** over $Y$ parameterized by the *mean* and *precision matrix*
>$$
>p(y) = \int_{x \in \mathbb{R}}p(x, y)dx = \mathcal{N}(y\,;\, \mu_{y},\, \left(\Theta / \Theta_{x x}\right)^{-1} ).
>$$

^fca789

>[!important] Proposition
>Then the **conditional p.d.f.** of $Y$ given $X$ is from a **normal distribution**
>$$
>p(y \,|\, x) = \mathcal{N}(y\,;\, \mu_{y|x},\, \Theta_{y y}^{-1}).
>$$
>where
>$$
>\begin{align*}
> \mu_{y|x} &= \mu_{y} - \Theta_{y y}^{-1}\,\Theta_{y x}\left(x - \mu_{x}\right) \\[3pt]
> &= \left(\mu_{y} +  \Theta_{y y}^{-1}\,\Theta_{y x}\mu_{x}\right) - \Theta_{y y}^{-1}\,\Theta_{y x}x  \\[8pt]
> \Theta_{y y} &= \Sigma_{y | x}^{-1}
>\end{align*}
>$$
>The *potential vector* of joint Gaussian is $\theta =\Sigma^{-1}\mu = \Theta\mu$  we have
>$$
>\begin{align*}
> \theta = \left[\begin{array}{c}
>\theta_{x}  \\
>\theta_{y} 
>\end{array}\right]  &= \left[\begin{array}{cc}
>\Theta_{x x} & \Theta_{x y} \\
>\Theta_{y x} & \Theta_{y y}
>\end{array}\right] \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right] 
>\end{align*}
>$$
>so
>$$
>\theta_{y} = \Theta_{y x}\mu_{x} + \Theta_{y y}\mu_{y}.
>$$
>
>We can find the *potential vector* for condition Gaussian distribution as
>$$
>\begin{align*}
>\theta_{y|x} &= \Sigma_{y | x}^{-1}\mu_{y|x} \\
>&=\Theta_{y y}\left( \mu_{y}+ \Theta_{y y}^{-1}\,\Theta_{y x}\mu_{x} - \Theta_{y y}^{-1}\,\Theta_{y x}x\right) \\
>&= \left( \Theta_{y y}\mu_{y} + \Theta_{y x}\mu_{x}\right) - \Theta_{y x}x \\[5pt]
>&= \theta_{y} - \Theta_{y x}x
>\end{align*}
>$$

^0d8021

- [[Partition of Matrix and Block Matrix]]
- [[Canonical Form of Gaussian Graphical Model]]





-----------
##  Recommended Notes and References


- [[Gaussian Random Variable]]
- [[Gaussian Process]]
- [[Gaussian Random Vector]]
- [[Gaussian Measure]]

- [[Conditional Probability]]
- [[Product Measure]]
- [[Probability Distribution of Random Variable]]

- [[Kalman Filter Discrete-Time]]

- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Positive Semidefinite Transformation]]

- Wikipedia [Multivariate_normal_distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)
- [[Matrix CookBook by Petersen]] pp 40 - 44