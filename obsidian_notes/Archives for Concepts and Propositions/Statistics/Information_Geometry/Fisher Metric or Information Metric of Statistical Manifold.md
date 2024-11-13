---
tags:
  - concept
  - math/information_geometry
  - statistics/inference
  - statistics/estimation
  - math/riemannian_geometry
keywords:
  - fisher_metric
  - information_metric
topics:
  - information_geometry
  - statistics/estimation
  - probabilistic_graphical_model
  - machine_learning_theory
name: Fisher Metric or Information Metric of Statistical Manifold
date of note: 2024-06-27
---

## Concept Definition

>[!important]
>**Name**: Fisher Metric or Information Metric of Statistical Manifold

![[Statistical Manifold as Parametric Family#^646891]]

![[Fisher Information#^03df64]]

>[!important] Definition
>Let  be a $n$-dimensional *statistical manifold* with *parameterization* $\theta\in \Theta$ on $\sigma$-finite measure space $(\mathcal{X}, \mathscr{F}, \mu)$.
>- Assume that $$\mathcal{S} \subset \mathcal{P}(\mathcal{X}) \subset L^2(\mathcal{X})$$ 
>- Note that for any random variables $X,Y\in L^2(\mathcal{X})$, $$\left\langle  X\,,\,Y  \right\rangle_{p} := \mathbb{E}_{ p }\left[  X Y\right]$$  
>- Denote $\ell_{\theta} := \log p_{\theta}$ as the *log-likelihood function*.
>  
>Given a point $p_{\theta}\in \mathcal{S}$ for $\theta\in \Theta$, the **Fisher information matrix** of $\mathcal{S}$ is a $n\times n$ matrix $$I(\theta) := [g_{i,j}(\theta)]$$ where
>- the $(i,j)$-entry is given by $$\begin{align*}I(\theta)_{i,j} := g_{i,j}(\theta) &=  \mathbb{E}_{ \theta }\left[ \frac{ \partial}{ \partial \theta^{i} }\ell\,\frac{ \partial}{ \partial \theta^{j}}\ell \right] \\[5pt] &= \int_{\mathcal{X}} \frac{ \partial}{ \partial \theta^{i} }\ell(\theta; x)\,\frac{ \partial}{ \partial \theta^{j} }\ell(\theta; x)\; p(x; \theta)\,d\mu(x) \\[5pt] &:= \left\langle \frac{ \partial}{ \partial \theta^{i} }\ell \,,\,  \frac{ \partial}{ \partial \theta^{j}}\ell  \right\rangle_{\theta} \end{align*}$$ 
>  
>Assume that $$\mathcal{B}_{\theta} := \left\{ \frac{ \partial}{ \partial \theta^{1} }\ell_{\theta} \,{,}\ldots{,}\, \frac{ \partial}{ \partial \theta^{n} }\ell_{\theta} \right\} \subset T_{p_{\theta}}\mathcal{S}$$  are *linearly independent* for each $\theta\in \Theta$.
>- In other word,  $\mathcal{B}_{\theta}$ form a **basis** of tangent space $T_{p}\mathcal{S}$ at $p_{\theta}$. 
>- Or, $\{ \partial_{1}\ell \,{,}\ldots{,}\, \partial_{n}\ell\}$ forms a **local frame** of *vector fields* on $T\mathcal{S}$.
>- This assumption means that the Fisher information $$I(\theta) \succ 0$$ is *positive definite* for each $\theta\in \Theta$.
>  
>Thus  the Fisher information matrix defines a *Riemannian metric*, $$g_{i,j} := \left\langle  \partial_{i}\ell\,,\, \partial_{j}\ell   \right\rangle, \quad i,j=1\,{,}\ldots{,}\,n.$$ It is called the **Fisher metric** or the **information metric.**

- [[Log-Likelihood Score Function and Fisher Score]]
- [[Statistical Manifold as Parametric Family]]
- [[Exponential Embedding and Representation of Tangent Space of Statistical Manifold]]
- [[Fisher Information]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Linear Independence]]
- [[Basis of Vector Space]]
- [[Local and Global Frame for Tangent Bundle]]


## Explanation


## Fisher Kernel

![[Positive Definite Kernel Examples#^b8f451]]

- [[Positive Definite Kernel Examples]]



-----------
##  Recommended Notes and References



- [[Exponential Family of Distributions]]

- [[Inner Product Space]]
- [[Hilbert Space]]


- [[Mathematical Statistics by Shao]] pp 171
- [[Methods of Information Geometry by Amari]] pp 28 - 31