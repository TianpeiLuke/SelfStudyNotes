---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/kernel_methods
keywords:
  - margin_based_loss
topics:
  - statistical_learning_theory
  - machine_learning_theory
name: Margin-based Generalization Error Bound for Kernel Hypothesis
date of note: 2024-08-01
---

## Concept Definition

>[!important]
>**Name**: Margin-based Generalization Error Bound for Kernel Hypothesis

![[Margin-based Loss Function#^a01095]]

![[Margin-based Loss Function#^19baca]]

- [[Margin-based Loss Function]]

### Margin Bounds for Binary Classification

![[Margin-based Generalization Error Bound#^e0b885]]

- [[Margin-based Generalization Error Bound]]

### Rademacher Complexity of Kernel-based Hypothesis

![[Rademacher Complexity#^8eafb1]]

![[Empirical Rademacher Complexity#^1a8bb4]]

- [[Rademacher Complexity Bound of Kernel-based Hypothesis]]

### Margin Bounds for Kernel-base Hypothesis

>[!important] Corollary
>Let $\mathcal{H}$ be a reproducing kernel Hilbert space of functions on $\mathcal{X}$ and $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$$ be a **positive definite kernel** and let $$\phi: \mathcal{X} \to \mathcal{H}$$ be a **feature mapping** associated with kernel $K$.
>- Assume that $$r^2 := \sup_{x\in \mathcal{X}}K(x, x)$$
>- Define the *$\lambda$-ball* of $\mathcal{H}$ be $$\mathcal{F}_{\lambda} := \left\{ f(x) := \left\langle  f\,,\,\phi(x) \right\rangle_{\mathcal{H}}\;:\; \lVert f \rVert_{\mathcal{H}} \le \lambda  \right\} \subset \mathcal{H}$$ for some $\lambda \ge 0.$
>- The **empirical margin loss** is defined as $$\widehat{L}_{\mathcal{D}, \rho}(h) := \frac{1}{n}\sum_{i=1}^{n}\phi_{\rho, \text{ramp}}(y_{i}\,h(x_{i}))$$ where $\phi_{\rho, \text{ramp}}$ is the *ramp loss*.
>
>Then, for any $\delta >0$, the following statements hold **with probability at least** $1- \delta$, for *any* $h\in \mathcal{F}_{\lambda}$
>- $$L(h) \le \widehat{L}_{\mathcal{D}, \rho}(h) + 2\sqrt{ \frac{r^2\, \lambda^2 / \rho^2}{n} } + \sqrt{ \frac{\log \left( 1 / \delta \right)}{2n} }$$ 
>- and $$L(h) \le \widehat{L}_{\mathcal{D}, \rho}(h) + 2\sqrt{ \frac{\text{tr}(K) \;\lambda^2 / \rho^2}{n} } + 3\sqrt{ \frac{\log \left( 2 / \delta \right)}{2n} }$$

^e0b885

- [[Rademacher Complexity Bound of Kernel-based Hypothesis]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]
- [[Rademacher Complexity]]
- [[Empirical Rademacher Complexity]]

### Maximum Mean Discrepancy Bound

>[!important] Theorem
>Let $\mathcal{H}$ be a reproducing kernel Hilbert space of functions on $\mathcal{X}$ and $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$$ be a **positive definite kernel** and let $$\phi: \mathcal{X} \to \mathcal{H}$$ be a **feature mapping** associated with kernel $K$.
>- Define the *$\lambda$-ball* of $\mathcal{H}$ be $$\mathcal{F}_{\lambda} := \left\{ f(x) := \left\langle  f\,,\,\phi(x) \right\rangle_{\mathcal{H}}\;:\; \lVert f \rVert_{\mathcal{H}} \le \lambda  \right\} \subset \mathcal{H}$$ for some $\lambda \ge 0.$
>- And $$\sup_{x\in \mathcal{X}}K(x, x) \le 1$$
>  
>Then *with probability at least* $1- \delta$, we have the bound for **maximum mean discrepancy (MMD)**
>$$
>\lVert \mu(\widehat{\mathcal{P}}_{n}) - \mu(\mathcal{P}) \rVert_{\mathcal{H}} \le 2 \sqrt{  \frac{\mathbb{E}_{ X\sim \mathcal{P} }\left[  K(X, X) \right]\;\lambda^2}{n} } + \sqrt{ \frac{2\log(1 / \delta)}{n} } 
>$$  
>where the **kernel mean embedding** of measure $\mathcal{P}$ and the empirical measure $\mathcal{P}_{n}$ is given by 
>$$
>\mu(\mathcal{P}) := \mathbb{E}_{ \mathcal{P} }\left[  \phi(X) \right],\; \quad \mu(\widehat{\mathcal{P}}_{n}) := \frac{1}{n}\sum_{i=1}^{n}\phi(x_{i})
>$$

^928a31

- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Kernel Mean Embedding of Distribution]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 34

>[!info]
>Note that both generalization error and empirical error can be represented as inner product with *kernel mean embedding*
>$$
> L_{\mathcal{P}}(h) := \mathbb{E}_{ \mathcal{P} }\left[  \mathbb{1}\left\{ Yh(X) < 0\right\}\right] :=  \left\langle  \mathbb{1} \circ h\,,\,  \mu(\mathcal{P})  \right\rangle_{\mathcal{H}}  
>$$
>and 
>$$
> \widehat{L}_{\mathcal{D}}(h) := \mathbb{E}_{\widehat{\mathcal{P}}_{n} }\left[  \mathbb{1}\left\{ Yh(X) < 0\right\}\right] :=  \left\langle  \mathbb{1} \circ h\,,\,  \mu(\widehat{\mathcal{P}}_{n}) \right\rangle_{\mathcal{H}}  
>$$


## Explanation



## SVM with Kernel

- [[Support Vector Machine Kernel Expansion and RKHS]]



-----------
##  Recommended Notes and References






- [[Positive Definite Kernel]]
- [[Feature Map for Reproducing Kernels in RKHS]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]


- [[AdaBoost Algorithm]]


- [[Foundations of Machine Learning by Mohri]] pp 119
- [[Boosting Foundations and Algorithms by Schapire]] pp 94 - 96
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] 