---
tags:
  - concept
  - machine_learning/theory
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - reproducing_kernel
topics:
  - machine_learning_theory
name: Reproducing Kernel in RKHS
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Reproducing Kernel in RKHS


![[Representation of Evaluational Functional in RKHS#^c84e79]]

- [[Representation of Evaluational Functional in RKHS]]
- [[Riesz Representation Theorem]]

>[!important] Definition
>Let $\mathcal{H} \subset \mathbb{C}^{X}$ be a *Hilbert space*. 
>
>A function $K:  X \times X \rightarrow \mathbb{C}$ is called a **reproducing kernel** (*r.k.*) of $\mathcal{H}$, if
>
>- For every $x \in X$, the kernel $K(x, \cdot)$ as a *function* belongs to $\mathcal{H}$; i.e., $$K(x, \cdot) := k_x \in \mathcal{H};$$ 
>- The **reproducing property**: for every $x \in X$ and every $f\in \mathcal{H}$,
>$$
> \begin{align}
> f(x) = \delta_x(f) &=  \left\langle f , k_{x} \right\rangle_{\mathcal{H}}  := \left\langle f , K(x, \cdot) \right\rangle_{\mathcal{H}} 
> \end{align} 
>$$ 
>

^8b1e73

- [[Hilbert Space]]
- [[Reproducing Kernel Hilbert Space]]

## Inner Product Representation


>[!important]  Inner Product Representation of. Reproducing Kernel
>By applying [[Riesz Representation Theorem]] on $K(x, \cdot)$ for each $x\in X$ evaluated at $y$, we have the **inner product representation** of **reproducing kernel**
>$$
>K(x, y) = \left\langle K(x, \cdot) ,  K(y, \cdot) \right\rangle_{\mathcal{H}}
>$$

- [[Riesz Representation Theorem]]

>[!info]
>This is called the **Kernel Theorem** or **Nuclear Theorem**. Similar results can be seen in **Nuclear space** 

- Wikipedia [Nuclear space](https://en.wikipedia.org/wiki/Nuclear_space)
- [[Functional Analysis by Reed]] pp145
- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Space of Tempered Distributions]]

## Explanation


>[!important] Equivalent Definition
>A *Hilbert space* equipped with a *reproducing kernel* $K$ is the **reproducing kernel Hilbert space**.
>
>Note that the reproducing property holds if and only if the evaluation functional $\delta_{x}$ is bounded linear functional.







-----------
##  Recommended Notes and References

- [[Riesz Representation Theorem]]
- [[Evaluation Functional]]
- [[Bounded Linear Functional]]
- [[Reproducing Kernel Hilbert Space]]



- [[Concepts and Theorems in Hilbert Space]]
- [[Concepts and Theorems in Statistical Learning Theory]]
- [[Concepts and Theorems for Gaussian Process]]


- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]] pp 4 - 16
- [[Learning with Kernels by Schölkopf]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 10 - 20


- [[Functional Analysis by Reed]]