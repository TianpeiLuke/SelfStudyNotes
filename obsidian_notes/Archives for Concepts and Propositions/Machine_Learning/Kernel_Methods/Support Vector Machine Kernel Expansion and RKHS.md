---
tags:
  - concept
  - machine_learning/models
  - machine_learning/theory
  - machine_learning/kernel_methods
keywords:
  - support_vector_machine
  - kernel_trick
  - reproducing_kernel_hilbert_space
topics:
  - machine_learning/kernel_methods
  - machine_learning_models
  - machine_learning_theory
name: Support Vector Machine Nonlinear Kernel and RKHS
date of note: 2024-10-08
---

## Concept Definition

>[!important]
>**Name**: Support Vector Machine Nonlinear Kernel and RKHS

![[Support Vector Machine General with Soft-Margin Relaxation#^5c5e42]]

![[Support Vector Machine General with Soft-Margin Relaxation#^80afee]]

![[Support Vector Machine General with Soft-Margin Relaxation#^1af93d]]

>[!important] Definition
>It is important to note that both the dual optimization problem 
>$$
>\begin{align*}
> \max_{\alpha}\;&\; \sum_{i=1}^{m}\alpha_{i} -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle \\[5pt]
> \text{s.t. }&\; \alpha_{i} \ge 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\; \sum_{i=1}^{m}\alpha_{i} y_{i} = 0
>\end{align*}
>$$
>and the solution 
>$$
> h(x) = \text{sgn}\left\{ \sum_{i=1}^{m}\alpha_{i} y_{i} \left\langle  x_{i}\,,\,x    \right\rangle + b \right\} 
>$$
>involves $\left\{ x_{i} \right\}$ only through the **inner products**. We can replace it with **reproducing kernels** in **Reproducing Kernel Hilbert Space** $\mathcal{H}$ to expand to the function $h\in \mathcal{H}$
>
>The technique that replaces inner product with *reproducing kernels* $K$ is called the **Kernel Trick.**

- [[Inner Product Space]]

![[Reproducing Kernel of RKHS#^8b1e73]]


>[!important] Definition
>Using **Kernel trick**, we can reformulate the *dual optimization problem* for *soft-SVM* using the *reproducing kernel* $$K: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$$  as 
>$$
>\begin{align*}
> \max_{\alpha}\;&\; \sum_{i=1}^{m}\alpha_{i} -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} K(x_{i}, x_{j}) \\[5pt]
> \text{s.t. }&\; \alpha_{i} \ge 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\; \sum_{i=1}^{m}\alpha_{i} y_{i} = 0.
>\end{align*}
>$$
>- The resulting model is called the **kernel Support Vector Machine (kernel SVM).**
>- The **optimal kernel SVM** is given by $$h(x) = \text{sgn}\left\{ \sum_{i=1}^{m}\alpha_{i} y_{i} K(x_{i}, x) + b \right\} $$
>	- $$\alpha_{i} = 0, \;\; \forall x_{i} \not\in \left\{ \text{support vectors} \right\}$$
>- By construction, the solution of kernel SVM lies in the **reproducing kernel Hilbert space (RKHS)** induced by kernel $K$ $$h\in \mathcal{H}_{K}$$

- [[Support Vector Machine General with Soft-Margin Relaxation]]
- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]

## Explanation

![[Representer Theorem#^315388]]

- [[Representer Theorem]]

>[!important]
>The **Representer theorem** states that the **Kernel SVM** is the minimizer of the *regularized risk problem* $$h \in \arg\min_{f\in \mathcal{H}} \sum_{i=1}^{m}L_{\text{hinge}}(y_{i}, f(x_{i})) + \frac{\lambda}{2}\lVert f \rVert_{\mathcal{H}}^2,$$
>where $\mathcal{H}$ is a *reproducing kernel Hilbert space*, and $$L_{\text{hinge}}(y, f(x)) = \max\left\{ 0, 1- y\,f(x) \right\}$$

- [[Hinge Loss as Surrogate Loss Function]]
- [[Regularized Loss Minimization]]
- [[Surrogate Loss Minimization]]

## Curse of Dimensionality

>[!quote]
>In the early literature on support vectors, there were claims that the kernel property of the support vector machine is unique to it and allows one to *finesse the curse of dimensionality*. **Neither of these claims is true**, and we go into both of these issues in the next three subsections.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 424






-----------
##  Recommended Notes and References



- [[Kernel Methods in Machine Learning by Hofmann]] pp 21 - 23
- [[Learning with Kernels by Schölkopf]] pp 200 - 203
- [[Elements of Statistical Learning by Hastie]] pp 417 - 421, 654, 657
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 171 - 177
- [[Foundations of Machine Learning by Mohri]] pp 87- 100

- [[Convex Optimization by Boyd]]
- [[Nonlinear Programming by Bertsekas]]