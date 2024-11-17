---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/kernel_methods
keywords:
  - reproducing_kernel
  - reproducing_kernel_hilbert_space
  - feature_map_kernel
  - positive_definite_kernel
  - rademacher_complexity
topics:
  - statistical_learning_theory
  - machine_learning_theory
name: Rademacher Complexity Bound of Kernel-based Hypothesis
date of note: 2024-08-01
---

## Concept Definition

>[!important]
>**Name**: Rademacher Complexity Bound of Kernel-based Hypothesis

![[Feature Map for Reproducing Kernels in RKHS#^8efea2]]

![[Rademacher Complexity#^8eafb1]]

![[Empirical Rademacher Complexity#^1a8bb4]]

>[!important] Theorem
>Let $\mathcal{H}$ be a reproducing kernel Hilbert space of functions on $\mathcal{X}$ and $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$$ be a **positive definite kernel** and let $$\phi: \mathcal{X} \to \mathcal{H}$$ be a **feature mapping** associated with kernel $K$.
>
>Let 
>-  $$\mathcal{D} = \left\{ x_{1} \,{,}\ldots{,}\, x_{n}\right\}  \subseteq \left\{ x\in \mathcal{X}:\; K(x, x) \le r^2 \right\} $$ be the set of i.i.d samples on $\mathcal{X}$
>- and the *$\lambda$-ball* of $\mathcal{H}$ be $$\mathcal{F}_{\lambda} := \left\{ f(x) := \left\langle  f\,,\,\phi(x) \right\rangle_{\mathcal{H}}\;:\; \lVert f \rVert_{\mathcal{H}} \le \lambda  \right\} \subset \mathcal{H}$$ for some $\lambda \ge 0.$
>  
>Then the **empirical Rademacher complexity** of $\mathcal{F}_{\lambda}$ with respect to sample $\mathcal{D}$ is bounded above by 
>$$
> \begin{align}
> \widehat{\mathfrak{R}}_{\mathcal{D}}(\mathcal{F}_{\lambda})&= \mathbb{E}_{ \epsilon }\left[ \sup_{f \in \mathcal{F}_{\lambda}}\frac{1}{n}\sum_{i=1}^{n}\epsilon_{i}f(X_i) \right] \le \frac{1}{n}\lambda\,\sqrt{ \text{tr}\left(K\right) } \le \sqrt{ \frac{r^2\;\lambda^2}{n} }
> \end{align}
>$$ 

^f07d78

- [[Positive Definite Kernel]]
- [[Feature Map for Reproducing Kernels in RKHS]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]

- [[Rademacher Complexity]]
- [[Empirical Rademacher Complexity]]


### Margin Bound

![[Margin-based Generalization Error Bound for Kernel Hypothesis#^e0b885]]

- [[Margin-based Generalization Error Bound]]
- [[Margin-based Generalization Error Bound for Kernel Hypothesis]]

## Explanation





-----------
##  Recommended Notes and References


- [[Rademacher Complexity Bound for Binary Classification]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Representer Theorem]]
- [[Support Vector Machine Kernel Expansion and RKHS]]


- [[Foundations of Machine Learning by Mohri]] pp 118
- [[Boosting Foundations and Algorithms by Schapire]] pp 94 - 96
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] 