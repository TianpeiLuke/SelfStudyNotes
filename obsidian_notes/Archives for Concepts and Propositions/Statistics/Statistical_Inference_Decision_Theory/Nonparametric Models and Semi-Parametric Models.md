---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - nonparametric_model
topics:
  - statistics/estimation
  - probability
name: Non-Parametric Models
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Non-Parametric Models

![[Parametric Models#^408b6c]]

- [[Parametric Models]]

>[!important] Definition
>A family of probability measures is said to a **nonparametric family** if it does not fit the definition of parametric family above.
>
>In particular, a set of *probability measures* $\mathcal{P}_{f}$ on $(\Omega, \mathscr{F})$ *indexed* by a *function* $f\in \mathcal{F}$ is said to be a **nonparametric family** if
>- $\mathcal{F}$ is a family of functions, i.e. $\mathcal{F}$ is **infinite-dimensional**, and
>- each $\mathcal{P}_{f}$ is known probability measure when $f\in \mathcal{F}$ fixed.
> 
>$$\mathscr{P} := \left\{ \mathcal{P}_{f}: f \in \mathcal{F} \right\}$$
> 
>The set $\mathcal{F}$ is called the **parameter space**.

- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]] pp 1
- [[Empirical Process and Empirical Measure]]
- [[Stochastic Process]]

>[!important] Definition
>A **nonparametric model** refers to the assumption that the *population* $\mathcal{P}$ is in a given nonparametric family.


>[!important] Definition
>In *statistical inference* and *decision theory*, methods designed for nonparametric models are called **nonparametric methods**.

>[!important] Definition
>A **semi-parametric model** refers to the assumption that the *population* $\mathcal{P}$ is in a given *nonparametric family* with *parametric component*.
>$$
>\mathscr{P} :=\left\{ \mathcal{P}_{(f, \theta)}: f \in \mathcal{F}, \theta\in \Theta  \right\} 
>$$

- [[Mathematical Statistics by Shao]] pp 96

## Explanation

>[!info]
>A nonparametric family is an **infinite-dimensional statistical manifold**.



## Statistical Sampling Models

- [[Concepts and Inequalities for Empirical Process]]


## Gaussian Noise Model

- [[Concepts and Theorems for Stochastic Differential Equations]]





-----------
##  Recommended Notes and References

- [[Population and Sample and Statistical Problem]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 95
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]] pp 1
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]