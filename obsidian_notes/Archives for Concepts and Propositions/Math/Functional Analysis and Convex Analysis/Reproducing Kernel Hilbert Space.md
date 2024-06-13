---
tags:
  - concept
  - machine_learning/theory
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - reproducing_kernel_hilbert_space
topics:
  - machine_learning_theory
name: Reproducing Kernel Hilbert Space
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Reproducing Kernel Hilbert Space (RKHS)

>[!important] Definition
>A *Hilbert space* $\mathcal{H} \subset \mathbb{C}^{X}$ is a **reproducing kernel Hilbert space** (**RKHS**) if, for all $x$ in $X$, *the evaluation functional* $\delta_x$ is a *bounded linear operator* on $\mathcal{H}$.
>
>That is, for every $x\in X$, there exists some $M_{x}>0$ such that 
>$$
> \begin{align*}
> \lvert \delta_x(f)  \rvert  := \lvert f(x) \rvert  \le M_{x}\lVert f \rVert_{\mathcal{H}} \qquad \forall f\in \mathcal{H}.\,
> \end{align*} 
>$$
> 
> Equivalently, for every $x\in X$, $\delta_x$ is *continuous* at *every* $f$ in $\mathcal{H}$. 

^8d2f94

- [[Hilbert Space]]
- [[Evaluation Functional]]
- [[Bounded Linear Functional]]
- [[Bounded Linear Operator and Norm of Operator]]

>[!important] Equivalent Definition 
>We say $\mathcal{H} \subset \mathbb{C}^{X}$ is a **reproducing kernel Hilbert space** (**RKHS**) on $X$ if 
>$$
>\delta_{x} \in \mathcal{H}^{*}, \quad \forall x\in X,
>$$
>where $\mathcal{H}^{*}$ is the **dual space** of $\mathcal{H}$.

- [[Dual Space of Hilbert Space]]

## Explanation

>[!important]
>The **boundedness assumption** on *evaluation functional* is **strong** since it requires that every function evaluated at every point is bounded.

## Reproducing Kernel

- [[Evaluation Functional]]
- [[Representation of Evaluational Functional in RKHS]]

![[Reproducing Kernel of RKHS#^8b1e73]]

- [[Reproducing Kernel of RKHS]]

>[!important] Equivalent Definition
>A *Hilbert space* equipped with a *reproducing kernel* $K$ is the **reproducing kernel Hilbert space**.
>
>Note that the reproducing property holds if and only if the evaluation functional $\delta_{x}$ is bounded linear functional.






-----------
##  Recommended Notes and References

- [[Evaluation Functional]]
- [[Bounded Linear Functional]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]



- [[Concepts and Theorems in Hilbert Space]]
- [[Concepts and Theorems in Statistical Learning Theory]]
- [[Concepts and Theorems for Gaussian Process]]


- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Understanding Machine Learning by Shalev-Shwartz]]


- [[Functional Analysis by Reed]]