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
>**Name**: Fisher Information

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

^03df64


- [[Parametric Models]]
- [[Probability Density Function of Random Variable]]

## Explanation

>[!important]
>Fisher information is **not available** for **nonparametric family**.

- [[Nonparametric Models and Semi-Parametric Models]]

>[!info]
>$$
>\begin{align*}
> I(\theta)_{i,j} &:=  \mathbb{E}_{ \mathcal{P}_{\theta} }\left[\frac{\partial}{ \partial \theta^i}\log f_{\theta}(X) \; \frac{\partial}{ \partial \theta^j}\log f_{\theta}(X)  \right] \\[10pt]
> &= \int_{\mathcal{X}}\,\left\{ \frac{\partial}{ \partial \theta^i}\log f_{\theta}(x) \; \frac{\partial}{ \partial \theta^j}\log f_{\theta}(x) \right\}\, f_{\theta}(x)\;d\mu(x).
>\end{align*}
>$$

>[!info]
>Consider $L^2(\mathcal{X}, \mu)$, the definition of Fisher information can be written in inner product form
>$$
> I(\theta) = \left\langle \frac{ \partial  }{ \partial \theta}\log f_{\theta}  ,  \frac{ \partial  }{ \partial \theta}\log f_{\theta} \right\rangle_{\mathcal{P}_{\theta}}
>$$

- [[Inner Product Space]]

## Cramér-Rao Lower Bound

![[Cramér-Rao Lower Bound#^71591b]]


>[!important]
>The **Cramér-Rao Lower Bound** states that $I(\theta)$ is a **measure** of the **information that $X$ contains about the unknown $\theta$**.
>
>-- [[Mathematical Statistics by Shao]] pp 170

- [[Cramér-Rao Lower Bound]]


## Alternative Form

>[!important] Proposition
>Suppose the random variable $X$ has p.d.f. $f_{\theta}$ that is **twice differentiable** in $\theta$ and the **regularity condition** holds
>$$\frac{ \partial  }{ \partial \theta}\int \frac{ \partial  }{ \partial \theta^{T} }f_{\theta}\,d\mu = \int \frac{\partial^2}{ \partial \theta\; \partial \theta^{T}} f_{\theta}\,d\mu, \quad \theta \in \Theta.$$ 
>
>Then the **Fisher information**  of parameter $\theta$ is 
>$$
>\begin{align*}
> I(\theta) =  -\mathbb{E}_{\mathcal{P}_{\theta}}\left[\,\frac{\partial^2}{ \partial \theta\; \partial \theta^{T}}\log f_{\theta}(X)\,\right].
>\end{align*}
>$$

- [[Mathematical Statistics by Shao]] pp 170

## Independence

>[!important] Proposition
>Let $X$ and $Y$ be **independent** and their **Fisher information matrices** are $I_{X}(\theta)$ and $I_{Y}(\theta)$, respectively. 
>
>Then the **Fisher information** about $\theta$ contained in $(X,Y)$ is $$I_{(X,Y)}(\theta) = I_{X}(\theta) + I_{Y}(\theta).$$
>
>In particular, if $X_{1} \,{,}\ldots{,}\,X_{n}$ are **i.i.d.**. and $I_{1}(\theta)$ is the Fisher information about $\theta$ in a single $X_{i}$, then **Fisher information** *about* $\theta$ *contained in* $X_{1} \,{,}\ldots{,}\,X_{n}$ is $$I_{(X_{1} \,{,}\ldots{,}\,X_{n})}(\theta) = n\,I_{1}(\theta).$$

- [[Mathematical Statistics by Shao]] pp 170

## Change of Variables

>[!important] 
>The **Fisher information** $I(\theta)$ depends on the particular **parameterization**.
>
>If $$\theta := \psi(\eta)$$ and $\psi$ is **differentiable**, then the *Fisher information* that $X$ *contains about $\eta$* is
>$$
>\frac{ \partial  }{ \partial \eta }\psi(\eta)\;\left[I\left( \psi(\eta)\right)  \right]\; \left( \frac{ \partial  }{ \partial \eta }\psi(\eta) \right)^T
>$$

## Perspective Function

- [[Perspective Function]]


## Fisher Information for Exponential Family


- [[Fisher Information for Exponential Family]]


## Riemannian Metric of Statistical Manifold

- [[Fisher Metric or Information Metric of Statistical Manifold]]
- [[Statistical Manifold as Parametric Family]]


>[!info]
>The Fisher information metric **fully characterizes the Riemannian geometry** of the parametric family 
>$$\mathscr{P}_{\Theta} := \left\{ \mathcal{P}_{\theta} \ll \mu: \theta \in \Theta \right\} = \left\{ f_{\theta} := \frac{d\mathcal{P}_{\theta}}{d\mu}: \theta \in \Theta   \right\} .$$

- [[Riemannian Metric and Riemannian Manifold]]





-----------
##  Recommended Notes and References




- [[Point Estimator]]

- [[Cumulative Distribution Function of Random Variable]]



- [[Methods of Information Geometry by Amari]]
- [[All of Statistics A Concise Course by Wasserman]]
- [[Elements of Information Theory by Cover]]
- [[Mathematical Statistics by Shao]] pp 169 - 171
