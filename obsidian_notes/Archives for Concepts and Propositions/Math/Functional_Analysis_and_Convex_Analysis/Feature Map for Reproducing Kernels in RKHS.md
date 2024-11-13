---
tags:
  - concept
  - math/functional_analysis
  - machine_learning/kernel_methods
keywords:
  - feature_map_kernel
topics:
  - functional_analysis
  - machine_learning/kernel_methods
name: Feature Map for Reproducing Kernels in RKHS
date of note: 2024-11-12
---

## Concept Definition

>[!important]
>**Name**: Feature Map for Reproducing Kernels in RKHS

>[!important] Definition
>Let $\mathcal{H}$ be a *reproducing kernel Hilbert space (RKHS)* of functions on $\mathcal{X}$ with kernel $K$. 
>
>A **feature map** is a map $$\phi: \mathcal{X} \to \mathcal{H}$$ such that 
>$$
>K(x, x') = \left\langle \phi(x) , \phi(x') \right\rangle_{\mathcal{H}}
>$$
>for any pair $x,x'$ in $\mathcal{X}$.
>- The **inner product representation** of $f\in \mathcal{H}$ *evaluated at* $x$ is given as $$\delta_{x}(f) := f(x) = \left\langle f , \phi(x) \right\rangle_{\mathcal{H}}$$ where $\delta_{x}$ is the *evaluation functional.*

^8efea2

- [[Reproducing Kernel Hilbert Space]]
- [[Representation of Evaluation Functional in RKHS]]
- [[Evaluation Functional]]

### Canonical Feature Map in Reproducing Kernel Hilbert Space

>[!important] Definition
>Let $\mathcal{H}$ be a *reproducing kernel Hilbert space (RKHS)* of functions on $\mathcal{X}$ with kernel $K$. 
>
>A **canonical feature map**  $$\phi: \mathcal{X} \to \mathcal{H}$$ is defined as 
>$$
>\phi(x) := K(x, \cdot).
>$$
>- Note that by *reproducing property*, $$f(x) = \left\langle f , K(x,\cdot)  \right\rangle_{\mathcal{H}} := \left\langle f , \phi(x)  \right\rangle_{\mathcal{H}} $$
>- $\phi(x)$ is a *function*, while $\phi(x)(x') := K(x, x')\in \mathbb{R}$ is a value.
>- A canonical feature map is also called a **reproducing kernel map**.

- [[Reproducing Kernel of RKHS]]

### Feature Map via Spectral Representation of Kernel

>[!important] Definition
>Let $\mathcal{H}$ be a *reproducing kernel Hilbert space (RKHS)* of functions on $\mathcal{X}$ with kernel $K$. 
>- By *Mercer's theorem*, there exists a *complete orthogonal basis* $\left\{ \psi_{i} \right\}$ in $\mathcal{H}$, corresponding to *eigenfunctions* associated with *non-negative eigenvalues* $\left\{ \lambda^{i} \right\}$ such that $$K = \sum_{i}\lambda^{i}\,\psi_{i}\otimes \psi_{i}$$
>
>A **Mercer feature map**  $$\phi: \mathcal{X} \to \ell^{2}$$ is defined as 
>$$
>\phi(x) := \left( \sqrt{ \lambda^{i} }\;\psi_{i}(x) \right)_{i=1}^{N_{K}}.
>$$
>where 
>- either $N_{K}\in \mathbb{N}$ or $N_{K} = \infty$.
>- $\phi(x)$ is a *sequence*.
>- This definition fits the **feature map** characterization $$K(x, x') = \left\langle \phi(x) , \phi(x') \right\rangle_{\ell^2}.$$
>- Note that since $\left\{ \psi_{i}/\sqrt{ \lambda^{i}} \right\}$ forms a *complete orthonormal basis* $\mathcal{H}$, for any $f\in \mathcal{H}$, we have $$f(x):= \sum_{i}\,f^{i}\,\frac{1}{\sqrt{ \lambda^{i}}}\psi_{i}(x) = \sum_{i}\,\frac{f^{i}}{\lambda^{i}}\,\sqrt{ \lambda^{i}}\psi_{i}(x).$$
>	- Let $$\hat{f} := (f^{i} / \lambda^{i}  )\in \ell^2$$ be the coordinate sequence of $f$ under basis $\left\{ \sqrt{ \lambda^{i} } \psi_{i} \right\}.$ 
>	- This leads to the **inner product representation** of $f\in \mathcal{H}$ $$f(x) = \left\langle \hat{f} , \phi(x) \right\rangle_{\ell^2}$$
>- This feature map is also called a **Mercer kernel map**.

- [[Positive Definite Kernel]]
- [[Mercer Theorem for Positive Definite Integral Kernels]]
- [[lp Sequence Space]]


## Explanation

>[!info]
>A **canonical feature map** is a **function-valued map** whose image is of **infinite dimension**.
>$$\phi(\mathcal{X}) \subset \mathcal{H}$$
>
>A **Mercer feature map** is a **vector-valued map** whose  image is of **high dimension** or **infinite dimension**
>$$
>\phi(\mathcal{X}) \subset \ell^2 \simeq \mathcal{H}
>$$

>[!important]
>The benefit of using **feature map** in RKHS is that it **separate function** $f$ from the **point** $x$ it evaluated at. 
>$$
>f(x) = \left\langle f , \phi(x) \right\rangle = \delta_{x}(f)
>$$
>- It provides an **inner prodcut representation** of **evaluation functional.**

- [[Representation of Evaluation Functional in RKHS]]

## Kernel Mean Embedding

![[Kernel Mean Embedding of Distribution#^300ada]]

- [[Kernel Mean Embedding of Distribution]]

## Covariance Operator

![[Covariance Operator in Reproducing Kernel Hilbert Space#^52cec0]]

- [[Covariance Operator in Reproducing Kernel Hilbert Space]]
- [[Covariance Operator]]


## Gaussian Process

- [[Gaussian Process]]
- [[RKHS of Gaussian Process]]
- [[RKHS of Gaussian Random Function]]



-----------
##  Recommended Notes and References



- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Functional Analysis by Reed]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 14
- [[Learning with Kernels by Schölkopf]] pp 32, 37
- [[Foundations of Machine Learning by Mohri]] pp 112 - 114, 117 - 119, 137, 
- [[Understanding Machine Learning by Shalev-Shwartz]]
