---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/kernel_methods
keywords:
  - representer_theorem
  - reproducing_kernel_hilbert_space
topics:
  - kernel_methods
  - machine_learning_theory
name: Representer Theorem
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: Representer Theorem

>[!important] Representer Theorem
>Let $\mathcal{X}$ be an index set, and  $\mathcal{H} \subset \mathbb{R}^{\mathcal{X}}$ be a *reproducing kernel Hilbert space*. Denote 
>- by $\Omega : [0, \infty) \to \mathbb{R}$ a **strictly monotonic increasing function**, and 
>- by $\ell : (\mathcal{X} \times \mathbb{R}^2)^m  \to \mathbb{R} \cup \{\infty\}$ an arbitrary *loss function*. 
>  
>Then each **minimizer** $f\in \mathcal{H}$ of the **regularized risk** 
>$$
>f \in \arg\min_{f\in \mathcal{H}} \left\{  \ell \left((x_{i}, y_{i}, f(x_{i})) \,{,}\ldots{,}\, (x_{m}, y_{m}, f(x_{m}))\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>admits a **representation** of the form
>$$
> f(x) = \sum_{i=1}^{m}\alpha_{i} K(x_{i}, x).
>$$

- [[Regularized Loss Minimization]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Representation of Evaluational Functional in RKHS]]
- [[Tikhonov Regularization in Optimization and Learning]]


## Explanation





-----------
##  Recommended Notes and References


- [[Regularized Loss Minimization]]
- [[Structural Risk Minimization]]

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]
- [[Support Vector Machine]]


- [[Kernel Methods in Machine Learning by Hofmann]] pp 16
- [[Learning with Kernels by Schölkopf]] pp 89

- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]