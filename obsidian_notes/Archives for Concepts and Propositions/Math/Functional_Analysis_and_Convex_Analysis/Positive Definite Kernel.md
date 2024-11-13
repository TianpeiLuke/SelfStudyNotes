---
tags:
  - concept
  - math/functional_analysis
  - machine_learning/kernel_methods
keywords:
  - positive_definite_kernel
topics:
  - functional_analysis
  - kernel_methods
name: Positive Definite Kernel
date of note: 2024-11-12
---

## Concept Definition

>[!important]
>**Name**: Positive Definite Kernel

>[!important] Definition
>Let $\mathcal{X}$ be an nonempty set. 
>
>A function $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$$ is called  a **positive definite kernel** if 
>- for any $n\in \mathbb{N}$, $\left\{ x_{1} \,{,}\ldots{,}\,x_{n}\right\} \subset \mathcal{X}$, the *Gram matrix*  is *positive semidefinite*,  $$K := [K(x_{i}, x_{j})]_{i,j=1}^{n} \succeq\,0.$$
>- A *positive definite kernel* is also called a **Mercer kernel.**

- [[Positive Semidefinite Transformation]]

>[!important] Definition
>Let $\mathcal{X}$ be an nonempty set. 
>
>A *complex-valued function* $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{C}$$ is called  a **positive definite kernel** if 
>- for any finite $n\in \mathbb{N}$, and any points $\left\{ x_{1} \,{,}\ldots{,}\,x_{n}\right\} \subset \mathcal{X}$,  and any complex numbers $\{ c_{1}\,{,}\ldots{,}\,c_{n} \} \subset \mathbb{C}$, 
>  $$
>  \sum_{i=1}^{n}\sum_{j=1}^{n}c_{i}\bar{c}_{j}\;K(x_{i}, x_{j}) \ge 0
> $$



### Positive Definite Operator

>[!important] Proposition
>For each **positive definite kernel** $K \in L^{\infty}(\mathcal{X}\times \mathcal{X}, \mu)$, there exists an *integral operator* on $L^2(\mathcal{X},\mu)$
>$$
>T_{K}: L^2(\mathcal{X},\mu) \to L^2(\mathcal{X},\mu),
>$$
>defined as 
>$$
>T_{k}f := \int_{\mathcal{X}}\,K(\cdot, x)\,f(x)\,d\mu(x),
>$$
>that is a **positive semi-definite operator** on $L^2(\mathcal{X},\mu)$. 
>- That is, for all $f\in L^{2}(\mathcal{X},\mu)$, $$\int_{\mathcal{X}}\int_{\mathcal{X}}\;K(x, x')\;f(x)\,f(x')\,d\mu (x)\,d\mu(x') \ge 0$$
>  
>Conversely, for every **positive semi-definite Hilbert-Schmidt operator** $$T\in \mathcal{B}_{HS}(\mathcal{X}), \quad T \succ\, 0,$$ there exists a **positive definite kernel** $K$ so that
>$$
> \begin{align*}
> (T f)(x) &= \int_{M}\, K(x, y)f(y)\; d\mu(y),
> \end{align*}
>$$   

- [[Positive Semidefinite Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Space of Hilbert-Schmidt Operators]]


## Explanation

>[!info]
>The term **kernel** for $K$ stems from the integral operator
>$$
>T_{k}f := \int_{\mathcal{X}}\,K(\cdot, x)\,f(x)\,d\mu(x),
>$$

>[!info]
>The *positive definite kernel* only requires the **positive semi-definiteness** of Gram matri.
>
>This mismatch is due to historical reason.


## Covariance Function

>[!info]
>Every **covariance function** for a Gaussian process corresponds to a **positive definite kernel.**

- [[Covariance Function of Gaussian Process]]
- [[RKHS of Gaussian Random Function]]


## Spectral Representation of Positive Definite Kernel

- [[Mercer Theorem for Positive Definite Integral Kernels]]



-----------
##  Recommended Notes and References



- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]] pp 4 - 16
- [[Learning with Kernels by Schölkopf]] pp 30
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 10 - 20
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 675