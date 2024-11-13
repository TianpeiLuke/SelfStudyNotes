---
tags:
  - concept
  - machine_learning/theory
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - reproducing_kernel_hilbert_space
  - evaluational_functional
  - riesz_representation_theorem
topics:
  - machine_learning_theory
name: Representation of Evaluation Functional in RKHS
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Representation of Evaluation Functional in RKHS

![[Reproducing Kernel Hilbert Space#^8d2f94]]
- [[Reproducing Kernel Hilbert Space]]

>[!important] Representation of Evaluational Functional in RKHS
>By [[Riesz Representation Theorem]], since $\delta_{x} \in \mathcal{H}^{*}$, there exists a **unique vector (function)** $k_{x} \in \mathcal{H}$ such that 
>$$
>\delta_{x} = \left\langle \cdot , k_{x} \right\rangle_{\mathcal{H}}.
>$$
>and
>$$
>\delta_{x}(f) = \left\langle f , k_{x} \right\rangle_{\mathcal{H}}.
>$$

^c84e79

- [[Evaluation Functional]]
### Integral Representation of Evaluation Functional

>[!important]
>Consider $\mathcal{H} = \mathcal{C}(T)$ where $T$ is **compact metric space**.  Since $\delta_{x} \in \mathcal{H}^{*}$ for each $x\in T$, by [[Riesz-Markov Representation Theorem]], there exists a *unique positive Radon measure* $\mu_{x}$ on $T$ such that 
>$$
>\delta_{x}(f) = f(x) = \int_{T} f(t)\,d\mu_{x}(t)
>$$
>Thus $\mu_{x}$ is the **Dirac measure** *at $x$*. We can identify $\mu_{x}$ with $\delta_{x}$
>$$
>f(x) = \int_{T} f(t)\,d\delta_{x}(t)
>$$

- [[Dirac Measure]]


## Explanation

>[!important]
>Since the evaluation functional $\delta_{x}$ depends on $x\in X$, the unique vector representation of $\delta_{x}$, i.e. $k_{x}$ *depends on* $x$ as well.
>
>That is, 
>$$
>k_{x}: X \to \mathbb{C}
>$$
>such that
>$$
>f(x) = \left\langle f , k_{x} \right\rangle_{\mathcal{H}}
>$$
>
>Moreover, we can find the **unique representation of $k_{x}$ itself**
>$$
>k_{x}(y) = \left\langle k_{x} , k_{y} \right\rangle_{\mathcal{H}}
>$$
>This property is called the **reproducing property**.

- [[Reproducing Kernel of RKHS]]







-----------
##  Recommended Notes and References

- [[Riesz Representation Theorem]]
- [[Evaluation Functional]]
- [[Bounded Linear Functional]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Reproducing Kernel Hilbert Space]]
- [[Hilbert Space]]



- [[Concepts and Theorems in Hilbert Space]]
- [[Concepts and Theorems in Statistical Learning Theory]]
- [[Concepts and Theorems for Gaussian Process]]


- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Understanding Machine Learning by Shalev-Shwartz]]


- [[Functional Analysis by Reed]]