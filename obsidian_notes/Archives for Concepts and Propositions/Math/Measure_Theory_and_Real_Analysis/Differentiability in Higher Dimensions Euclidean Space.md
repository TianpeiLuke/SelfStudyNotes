---
tags:
  - concept
  - math/calculus
keywords:
  - differential_mutivariate
topics:
  - calculus
  - real_analysis
name: Differentiability in Higher Dimensions Euclidean Space
date of note: 2024-11-02
---

## Concept Definition

>[!important]
>**Name**: Differentiability in Higher Dimensions Euclidean Space

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}^{m}$ is said to be **differentiable** *at* $x_{0}\in \mathbb{R}^{n}$ if there exists a *linear map* $$\ell: \mathbb{R}^{n} \to \mathbb{R}^{m}$$ such that
>$$
>\lim_{ h \to 0 } \frac{\lVert f(x_{0} + h) - f(x_{0}) - \ell(h) \rVert_{\mathbb{R}^{m}} }{\lVert h \rVert_{\mathbb{R}^{n}} } = 0.
>$$
>- If $f$ is **differentiable** at $x_{0}$, then all of its **partial derivatives** *exist* $$\frac{ \partial f }{ \partial x^{i} }(x_{0})$$
>- The linear map $\ell$ is called the **differential** of $f$, 
>- The differential of $f$ is given by the **Jacobian matrix** $$Df := \frac{ \partial f }{ \partial x } :=  \frac{ \partial (f^1 \,{,}\ldots{,}\,f^{m}) }{ \partial (x^{1} \,{,}\ldots{,}\,x^{n}) } $$

- [[Jacobian Matrix and Jacobian Determinant]]


## Explanation



## Functional Extension

![[Fréchet Derivative and Strong Derivative in Banach Space#^8e4985]]

- [[Fréchet Derivative and Strong Derivative in Banach Space]]







-----------
##  Recommended Notes and References


- [[Differentiability in One Dimensions Euclidean Space]]


- [[Principles of Mathematical Analysis by Rudin]]