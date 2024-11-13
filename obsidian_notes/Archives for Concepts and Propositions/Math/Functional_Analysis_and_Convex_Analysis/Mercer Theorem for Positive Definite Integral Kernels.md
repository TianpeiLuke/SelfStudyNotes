---
tags:
  - concept
  - math/functional_analysis
  - machine_learning/theory
  - machine_learning/kernel_methods
keywords:
  - mercer_theorem
  - positive_semidefinite_operator
  - positive_definite_kernel
  - reproducing_kernel_hilbert_space
topics:
  - functional_analysis
  - machine_learning_theory
  - machine_learning/kernel_methods
name: Mercer Theorem for Positive Definite Integral Kernels
date of note: 2024-05-10
---

## Theorem

>[!important]
>**Name**:  Mercer's Theorem for Positive Definite Kernels

>[!important] Mercer's Theorem
>Suppose $\Omega$ is a **compact domain** and $T$ is a **positive Hilbert-Schmidt operator** on $L^2(\Omega)$. 
>
>If the **integral kernel** $K(\cdot, \cdot)$ is **continuous** on $\Omega \times \Omega$, then the **eigenfunction** $\varphi_k$ is **continuous** on $\Omega$ if $\lambda_k > 0$, and the expansion
>$$
> \begin{align*}
> K(x,y) &= \sum_{n=1}^{\infty}\lambda_{n}\varphi_n(x)\overline{\varphi_n(y)}
> \end{align*}
>$$
> converges **uniformly** on **compact sets.**

- [[Positive Semidefinite Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]

- [[Compact Operator]]
- [[Space of Bounded Linear Operators]]

>[!important] Mercer's Theorem
>Let $\mathcal{X}$ be **compact Hausdorff** space and $\mu$ be a *$\sigma$-finite Borel measure* on $\mathcal{X}$
>
>Let $K\in L^{\infty}(\mathcal{X}, \mathcal{X})$ be a **symmetric**, **continuous positive definite** kernel. 
>- The **integral operator** $$T_{k}: L^{2}(\mathcal{X}, \mu) \to L^{2}(\mathcal{X}, \mu)$$ defined as $$(T_{k}f)(x) := \int_{\mathcal{X}}K(x, x')f(x')\,d\mu(x'),$$ is **positive definite.** That is, for all $f\in L^{2}(\mathcal{X},\mu)$, $$\int_{\mathcal{X}}\int_{\mathcal{X}}\;f(x)\,f(x')\,K(x, x')d\mu (x)\,d\mu(x') \ge 0$$
>
>  
>Then 
>- There exists a **complete orthogonal basis** $\left\{ \psi_{i} \right\}_{i=1}^{\infty}$ for $T_{k}$ in $L^{2}(\mathcal{X}, \mu)$ consisting of **eigenfunctions** associated with *non-negative eigenvalues* $\left\{ \lambda^{i} \right\}_{i=1}^{\infty}$, i.e. $$\lambda_{i} \ge 0.$$
>- The *eigenfunctions* $\left\{ \psi_{i} \right\}_{i=1}^{\infty}$ corresponding to nonzero eigenvalues are **continuous** on $\mathcal{X}$
>- The sequence of *eigenvalues* is **$\ell_{2}$-convergent** $$\left( \lambda^{i} \right)_{i=1}^{\infty} \in \ell_{2} \implies \sum_{i=0}^{\infty}|\lambda^{i}|^{2}  < \infty  $$  
>- The kernel function $K$ can be *represented* as $$K(x, x') = \sum_{i=1}^{\infty}\lambda^{i}\,\psi_{i}(x)\,\psi_{i}(x')$$ where 
>	- the series *converges* **absolutely and uniformly** for **almost every**  $(x,x')$ i.e. $$\text{ess}\sup_{(x,x')}\left\lvert \sum_{i=1}^{N_{K}}\lambda^{i}\,\psi_{i}(x)\,\psi_{i}(x') - K(x, x') \right\rvert \stackrel{N_{K}\to \infty}{\longrightarrow} 0$$ or $$\left\lVert \sum_{i=1}^{N_{K}}\lambda^{i}\,\psi_{i}\otimes\psi_{i} - K \right\rVert_{L^{\infty}} \to \infty$$

- [[Positive Definite Kernel]]
- [[Lp Space]]
- [[lp Sequence Space]]
- [[Compact Hausdorff Space]]
- [[Uniformly Almost Everywhere Convergence]]

## Explanation

>[!info]
>By definition, the operator 
> $$(T_{k}f)(x) := \int_{\mathcal{X}}K(x, x')f(x')d\mu(x'),$$
> is a **self-adjoint, compact operator**.
> 
> Thus by **Hilbert-Schmidt theorem**, there exists a **complete orthonormal basis** $\left\{ \psi_{i} \right\}$ for $T_{k}$


- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]
- [[Self-Adjoint Operator in Hilbert Space]]
- [[Compact Operator]]
- [[Hilbert-Schmidt Operator]]

>[!info]
>Since $\left\{ \psi_{i} \right\}$ are eigenfunctions for $\left\{ \lambda^{i} \right\}$, we can formulate the **complete orthonormal basis** for $L^2$ space as
>$$
>\left\{ \frac{1}{\sqrt{ \lambda_{i} }}\psi_{i}, \quad i=1 \,{,}\ldots{,}\, \infty \right\}
>$$

- [[Complete Orthonormal Basis of Hilbert Space]]

>[!important]
>*Mercer's theorem* provide the **spectral representation** of a **positive definite kernel** $K$ using the *spectral representation* of the corresponding **integral operator**
>$$
> K   \iff T_{K} := \int_{\mathcal{X}} K\,\cdot\,d\mu
>$$ 
>Then 
>$$
>K = \sum_{i}\,\lambda^{i}\,\psi_{i}\otimes\psi_{i} \iff T_{K} = \sum_{i}\,\lambda^{i} \,P_{\psi_{i}}
>$$
>or
>$$
>K \in \bigoplus_{i=1}^{\infty} \text{span}\left\{\psi_{i}\otimes\psi_{i}  \right\}
>$$

- [[Spectral Theorem in Projection-Valued Measure Form]]
- [[Integral Operator associated with Transition Kernel]]


### Diagonal of Tensor Product Space

>[!important]
>**Mercer's theorem** confirms that the *space of all positive definite kernels* $K\in \mathcal{L}(\mathcal{H}, \mathcal{H})$ is **isomorphic** to the **diagonal of tensor product space** 
>$$
>\left\{ K\in \mathcal{L}(\mathcal{H}, \mathcal{H}):\; T_{K} \succ\, 0 \right\} \simeq \text{diag}\left(\mathcal{H}\otimes \mathcal{H}\right) := \left\{ \sum_{i}\alpha^{i} \,\psi_{i}\otimes \psi_{i} \right\} 
>$$
>- Specifically, the *isomophism* is defined as a map 
>$$\sum_{i}\psi_{i}\otimes \psi_{i} \to T_{K} := \sum_{i}\left\langle \cdot , \psi_{i} \right\rangle_{\mathcal{H}}\,\psi_{i} $$
>- The **tensor diagonal** space is obtained as 

- [[Symmetric Tensor]]
- [[Tensor Product]]



-----------
##  Recommended Notes and References


- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]

- [[Bounded Linear Functional]]
- [[Lp Space]]
- [[Compactness]]

- [[Radon Measure]]
- [[Borel Measure]]

- [[Representation of Gaussian Random Function in Hilbert Space]]


- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Functional Analysis by Reed]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 14
- [[Learning with Kernels by Schölkopf]] pp 37
- [[Foundations of Machine Learning by Mohri]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 684
- [[Lectures on Gaussian Processes by Lifshits]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)