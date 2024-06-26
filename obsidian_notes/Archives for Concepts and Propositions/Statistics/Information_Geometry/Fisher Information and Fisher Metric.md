---
tags:
  - concept
  - statistics/estimation
  - math/information_geometry
keywords:
  - fisher_information
  - fisher_metric
topics:
  - information_geometry
  - statistics/estimation
name: Fisher Information and Fisher Metric
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Fisher Information and Fisher Metric

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *$\sigma$-finite measure space.*
>
>Suppose that $X = (X_{1} \,{,}\ldots{,}\,X_{n})$ is a sample from a **parametric model** $$\mathcal{P} \in \mathscr{P}_{\Theta} := \left\{ \mathcal{P}_{\theta} \ll \mu: \theta \in \Theta \right\},$$ where $\Theta \subset \mathbb{R}^d$ is an *open subset*. The p.d.f. with respect to $\mu$, $$f_{\theta} = \frac{d\mathcal{P}_{\theta}}{d\mu}$$ is *differentiable* as a function of $\theta$. 
>
> The **Fisher information matrix** of parameter $\theta$ is defined by
>$$
>\begin{align*}
> I(\theta) =  \mathbb{E}_{\mathcal{P}_{\theta}}\left[\frac{\partial}{ \partial \theta}\log f_{\theta}(X)\, \left[ \frac{\partial}{ \partial \theta}\log f_{\theta}(X) \right]^{T}  \right],
>\end{align*}
>$$
>that is for any $i,j=1 \,{,}\ldots{,}\,d$,
>$$
> I(\theta)_{i,j} :=  \mathbb{E}_{ \mathcal{P}_{\theta} }\left[\frac{\partial}{ \partial \theta^i}\log f_{\theta}(X) \; \frac{\partial}{ \partial \theta^j}\log f_{\theta}(X)  \right].
>$$
>
>If $f_{\theta}$ is second-order differentiable

- [[Parametric Models]]


## Explanation

>[!important]
>Fisher information is **not available** for **nonparametric family**.

- [[Nonparametric Models and Semi-Parametric Models]]


## Riemannian Metric of Statistical Manifold


- [[Statistical Manifold of Parametric Family]]


>[!info]
>The Fisher information metric **fully characterizes the Riemannian geometry** of the parametric family 
>$$\mathscr{P}_{\Theta} := \left\{ \mathcal{P}_{\theta} \ll \mu: \theta \in \Theta \right\}.$$

- [[Riemannian Metric and Riemannian Manifold]]



-----------
##  Recommended Notes and References


- [[Riemannian Metric and Riemannian Manifold]]
- [[Inner Product Space]]

- [[Point Estimator]]
- [[Log-Likelihood Score Function]]
- [[Statistical Manifold of Parametric Family]]
- [[Cumulative Distribution Function of Random Variable]]



- [[Methods of Information Geometry by Amari]]
- [[All of Statistics A Concise Course by Wasserman]]
- [[Elements of Information Theory by Cover]]
