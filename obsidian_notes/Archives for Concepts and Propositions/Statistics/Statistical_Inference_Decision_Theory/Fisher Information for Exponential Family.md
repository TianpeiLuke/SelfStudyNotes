---
tags:
  - concept
  - math/information_geometry
  - statistics/estimation
keywords:
  - fisher_information
  - exponential_family
topics:
  - statistics/estimation
  - information_geometry
name: Fisher Information for Exponential Family
date of note: 2024-06-27
---

## Concept Definition

>[!important]
>**Name**: Fisher Information for Exponential Family

>[!important] Propostiion
>Suppose that the distribution of $X$ is from an **exponential family** $\mathscr{P}_{\Theta} := \left\{ f_{\theta}: \theta\in \Theta \right\}$, i.e.the p.d.f. of $X$ with respect to a *$\sigma$-finite measure* $\nu$ is
>$$
> f_{\theta}(x) := \exp\left( \left\langle  \eta(\theta)\,,\, T(x)   \right\rangle - A(\theta) \right)\;h(x) 
>$$
>where $\theta \in \Theta \subset \mathbb{R}^d.$
>
>- Then the **regularity condition** $$\frac{ \partial  }{ \partial \theta}\int_{\mathcal{X}} g\,f_{\theta}\,d\nu = \int_{\mathcal{X}} g\,\frac{ \partial  }{ \partial \theta }f_{\theta}\,d\nu, \quad \theta \in \Theta,$$ **holds for any** $g$ such that $$ \mathbb{E}_{ f_{\theta} }\left[ g(X) \right] = \int_{\mathcal{X}}g\,f_{\theta}\,d\nu < \infty.$$
>- If $I(\eta)$ is the **Fisher information** for the **natural parameter** $\eta$, then the **variance-covariance matrix** of *statistic* $T$ is $$\text{Cov}(T, T) = I(\eta).$$
>- If  $I(\mu)$ is the **Fisher information** for the **mean parameter** $\mu$, $$\mu :=  \mathbb{E}_{ f_{\theta} }\left[\,T(X)\,\right]$$ Then the **variance-covariance matrix** of *statistic* $T$ is $$\text{Cov}(T, T) = \left[  I(\mu) \right]^{-1}.$$

^713d66

- [[Fisher Information]]
- [[Exponential Family of Distributions]]
- [[Mathematical Statistics by Shao]] pp 171

## Proof

### Part 2

![[Log-Partition Function of Exponential Family#^8780a9]]

- [[Log-Partition Function of Exponential Family]]

![[Exponential Family of Distributions#^c95a01]]

![[Exponential Family of Distributions#^c37891]]



## Explanation





-----------
##  Recommended Notes and References


- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function of Exponential Family]]
- [[Fisher Information]]


- [[Mathematical Statistics by Shao]] pp 171
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]