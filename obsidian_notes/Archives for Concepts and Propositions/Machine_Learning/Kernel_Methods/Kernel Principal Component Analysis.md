---
tags:
  - concept
  - machine_learning/kernel_methods
  - machine_learning/dimensionality_reduction
  - kernel_principal_component_analysis
  - kpca
keywords:
  - kernel_pca
  - principle_component_analysis
topics:
  - machine_learning/dimensionality_reduction
  - machine_learning/kernel_methods
name: Kernel Principal Component Analysis
date of note: 2024-11-05
---

## Concept Definition

>[!important]
>**Name**: Kernel Principal Component Analysis

![[Principal Component Analysis or PCA#^feea32]]

>[!important] Definition
>Let $\mathcal{D} := \{x_{1}\,{,}\ldots{,}\,x_{n}\}$ be i.i.d. samples from $\mathcal{P}(x)$ on $\mathcal{X}$. 
>
>Let $\mathcal{H}$ be the *reproducing kernel Hilbert space (RKHS)* with kernel $K$. Denote $\phi: \mathcal{X} \to \mathcal{H}$ as the *canonical feature map* i.e. $$\phi(x) := K(x, \cdot)$$ such that $$f(x) = \left\langle f , \phi(x) \right\rangle_{\mathcal{H}}, \quad \forall f\in \mathcal{H}.$$
>- Assume that $$ \mathbb{E}_{P}\left[ f(X) \right] = 0.$$
>- Define the *variance* of $f(X)$ over samples $\mathcal{D}$ as $$\text{Var}(f)  := \mathbb{E}\left[ f^2(X) \right] = \mathbb{E}\left[ \left\langle f , \phi(X) \right\rangle_{\mathcal{H}}^2 \right] $$
>
>The **kernel principal component analysis (kernel PCA)** is given by 
>$$
>\begin{align*}
> \max_{f\in \mathcal{H}} \;&\; \text{Var}(f) \\[5pt]
> \text{s.t. }&\; \lVert f \rVert_{\mathcal{H}} \le 1  
>\end{align*}
>$$


- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Feature Map for Reproducing Kernels in RKHS]]

### Kernel PCA via Covariance Operator in RKHS

![[Covariance Operator in Reproducing Kernel Hilbert Space#^39f1ad]]

![[Covariance Operator in Reproducing Kernel Hilbert Space#^52cec0]]


>[!important] Definition
>Let $\mathcal{D} := \{x_{1}\,{,}\ldots{,}\,x_{n}\}$ be i.i.d. samples from $\mathcal{P}(x)$ on $\mathcal{X}$. 
>
>Let $\mathcal{H}$ be the *reproducing kernel Hilbert space (RKHS)* with kernel $K$. Denote $\phi: \mathcal{X} \to \mathcal{H}$ as the *canonical feature map* i.e. $$\phi(x) := K(x, \cdot)$$ such that $$f(x) = \left\langle f , \phi(x) \right\rangle_{\mathcal{H}}, \quad \forall f\in \mathcal{H}.$$
>
>Define the *covariance operator* in $\mathcal{H}$ as $$\mathcal{K} :=  \mathbb{E}_{X}\left[\phi(X) \otimes \phi(X)\right]$$
>- Given samples in $\mathcal{D}$, the *sample covariance operator* is given by a *symmetric 2-tensor* $$\widehat{\mathcal{K}} = \frac{1}{n}\sum_{j=1}^{n}\phi(x_{j})\,\phi(x_{j}) \in \mathcal{H}\otimes \mathcal{H}$$ 
>- For any $x, x'\in \mathcal{X}$, $$\hat{\mathcal{K}}(x, x') := \frac{1}{n}\sum_{i=1}^{n}K(x_{i},x)\,K(x_{i},x')$$
>- The *sample covariance operator* is identified with the map $\mathcal{K}: \mathcal{H} \to \mathcal{H}$ in $\mathcal{H}$ such that $$\widehat{\mathcal{K}}f = \frac{1}{n}\sum_{j=1}^{n}\left\langle f , \phi(x_{j}) \right\rangle_{\mathcal{H}}\,\phi(x_{j}) = \frac{1}{n}\sum_{j=1}^{n}f(x_{j})\,\phi(x_{j})$$
>- This is equivalent to the definition $\mathcal{K}: \mathcal{H} \to \mathcal{H}$  so that $$\left\langle f , \mathcal{K}\,f \right\rangle_{\mathcal{H}} = \text{Var}(f(X))$$
>  
>The **kernel principal component analysis (kernel PCA)** find the optimal $f\in \mathcal{H}$ given $\mathcal{D}$ such that 
>$$
>\begin{align*}
> \max_{f\in \mathcal{H}} \;&\; \left\langle f , \mathcal{K}\,f \right\rangle_{\mathcal{H}} \\[5pt]
> \text{s.t. }&\; \lVert f \rVert_{\mathcal{H}} \le 1  
>\end{align*}
>$$
>- The Lagrangian is given by $$\left\langle f , \mathcal{K}\,f \right\rangle_{\mathcal{H}} - \lambda\,\lVert f \rVert_{\mathcal{H}}^2$$
>- **Kernel PCA** concerns of the following *eigenvalue problem* in $\mathcal{H}$
>$$
>\begin{align*}
>\left\langle \phi(x_{i}) , \widehat{\mathcal{K}}\,f \right\rangle_{\mathcal{H}}  &= \lambda \;\left\langle \phi(x_{i}) , f \right\rangle_{\mathcal{H}}, \quad i=1\,{,}\ldots{,}\, n
>\end{align*}
>$$
>- By *representer theorem*, we can represent $$f = \sum_{i=1}^{n}\alpha_{i}\phi(x_{i})$$
>- The above problem becomes 
>$$
>\begin{align*}
>\sum_{j=1}^{n}\alpha_{j}\;\left\langle \phi(x_{i}) , \widehat{\mathcal{K}}\,\phi(x_{j}) \right\rangle_{\mathcal{H}}  &= \lambda \;\sum_{j=1}^{n}\alpha_{j}\,\left\langle \phi(x_{i}) , \phi(x_{j}) \right\rangle_{\mathcal{H}}, \quad i=1\,{,}\ldots{,}\, n \\[8pt]
> \iff \sum_{j=1}^{n}\alpha_{j}\;\left\langle \phi(x_{i}) , \frac{1}{n}\sum_{s=1}^{n}\left\langle \phi(x_{j}) , \phi(x_{s}) \right\rangle_{\mathcal{H}}\,\phi(x_{s}) \right\rangle_{\mathcal{H}}  &= \lambda \;\sum_{j=1}^{n}\alpha_{j}\,\left\langle \phi(x_{i}) , \phi(x_{j}) \right\rangle_{\mathcal{H}}  \\[8pt]
> \iff K^2\alpha &= n\,\lambda\,K\alpha
>\end{align*}
>$$
>- In other word, the **kernel PCA** solves the *eigenvalue problem*
>$$
>K\alpha = n\,\lambda\,\alpha
>$$
>where the *Gram matrix* is defined as
>$$K := [K(x_{i}, x_{j})] \in \mathbb{R}^{n\times n}$$ and the constraints on $\alpha$ is $$\lVert \alpha \rVert \le 1 $$
>- The optimal solution $\alpha^{*}$ is the **principal component direction** corresponding to the $1$st-**principal component** of kernel matrix $K$

- [[Covariance Operator in Reproducing Kernel Hilbert Space]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Methods of Lagrangian Multipliers]]
- [[Symmetric Tensor]]
- [[Principal Component Analysis or PCA]]

![[kernel_pca.png]]

## Explanation

### Eigenvalue Problem for Compact Operator in RKHS

>[!important]
>The kernel PCA concerns the following **functional eigenvalue problem**
>$$
>\mathcal{K}\,f = \lambda\,f
>$$
>where $\mathcal{K}: \mathcal{H}\to \mathcal{H}$ is the *covariance operator* in RKHS $\mathcal{H}$.
>- Note that $\mathcal{K}$ is a *self-adjoint, compact* bounded linear operator.
>- By *Hilbert-Schimidt theorem*, we can find a complete orthonormal basis (**spectral basis**) $\left\{ \psi_{i} \right\}$ so that 
>$$
>\mathcal{K}\,\psi_{i} = \lambda^{i}\,\psi_{i}, \quad i=1\,{,}\ldots{,}\,\infty
>$$
>- $\mathcal{K}$ is identified as a **symmetric 2-tensor** $$\mathcal{K} =  \sum_{i=1}^{\infty}\lambda^{i}\; \mathbb{E}_{ X }\left[ \psi_{i}(X)\otimes \psi_{i}(X) \right]$$
>- Finally, we can find the **spectral representation** of $\mathcal{K}f$ under the  complete orthonormal basis $\left\{ \psi_{i} \right\}$ as $$\mathcal{K}f = \sum_{i=1}^{\infty} \lambda^{i}\,\left\langle f , \psi_{i} \right\rangle_{\mathcal{H}}\,\psi_{i} = \sum_{i=1}^{\infty}\lambda^{i}\,f^{i}\,\psi_{i}$$ where $\left\{ f^{i} \right\}$ are coordinate of $f$ under basis $\left\{ \psi_{i} \right\}$ i.e. $$f = \sum_{i=1}^{\infty}f^{i}\,\psi_{i}$$
>  
>The kernel eigenvalue problem $$K\alpha = \lambda \alpha$$ corresponds to the above problem **restricted** to $n$ samples in $\mathcal{D}$.  
>- $$
>\begin{align*}
>\left\langle \phi(x_{i}) , \widehat{\mathcal{K}}\,f \right\rangle_{\mathcal{H}}  &= \lambda \;\left\langle \phi(x_{i}) , f \right\rangle_{\mathcal{H}}, \quad i=1\,{,}\ldots{,}\, n \\[10pt]
> \iff \left( \widehat{\mathcal{K}}\,f \right)(x_{i}) &= \lambda\,f(x_{i})
>\end{align*}
>$$

- [[Covariance Operator in Reproducing Kernel Hilbert Space]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]
- [[Spectral Theorem in Functional Calculus Form]]
- [[Spectral Theorem in Projection-Valued Measure Form]]


### Nonlinear Dimensionality Reduction in RKHS

>[!important] 
>The **kernel PCA** is a **nonlinear dimensionality reduction**.  It *reduces the dimensionality* of samples $x$ using *transformation* from *RKHS* $\mathcal{H}$. 
>- In particular, let $f\in \mathcal{H}_{X}$ be the map $$x \mapsto f(x) = z$$ defined a **nonlinear encoder**
>- We also define a map $g\in \mathcal{H}_{Z}$ $$z \mapsto g(z)$$ as the corresponding **nonlinear decoder**.


- [[Principal Component Analysis or PCA]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]




-----------
##  Recommended Notes and References




- [[Probabilistic Principal Component Analysis]]

- [[Spectral Theorem in Projection-Valued Measure Form]]


- [[Compact Operator]]

- [[Elements of Statistical Learning by Hastie]] pp 547 - 550
- [[Learning with Kernels by Schölkopf]] pp 429 - 442,
- [[Kernel Methods in Machine Learning by Hofmann]] pp 41 - 42, 
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 99
- [[Foundations of Machine Learning by Mohri]] pp 347, 349–354, 356, 357
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 281

