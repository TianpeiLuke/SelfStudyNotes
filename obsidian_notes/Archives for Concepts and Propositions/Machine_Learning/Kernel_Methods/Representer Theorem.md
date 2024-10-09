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

^315388

- [[Regularized Loss Minimization]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Representation of Evaluational Functional in RKHS]]
- [[Tikhonov Regularization in Optimization and Learning]]

### Semi-Parametric Representer Theorem

>[!important] Semi-Parametric Representer Theorem
>Let $\mathcal{X}$ be an index set, and  $\mathcal{H} \subset \mathbb{R}^{\mathcal{X}}$ be a *reproducing kernel Hilbert space*. Denote 
>- by $\Omega : [0, \infty) \to \mathbb{R}$ a **strictly monotonic increasing function**, and 
>- by $\ell : (\mathcal{X} \times \mathbb{R}^2)^m  \to \mathbb{R} \cup \{\infty\}$ an arbitrary *loss function*. 
>- Assume that there are a set of $M$ real-valued functions $$\psi_{p}: \mathcal{X} \to \mathbb{R},\quad p =1\,{,}\ldots{,}\,M$$ with property that the $m\times M$ matrix $$(\psi_{p}(x_{i}))_{i\in [m], p\in [M]}$$ has **rank** $M$.  
>  
>Then any $$\widetilde{f} := f + h, \quad f\in \mathcal{H}, \; h\in \text{span}\left\{ \psi_{p}, p\in [M] \right\} $$ that **minimizes** the **regularized risk** 
>$$
>\widetilde{f}  \in \arg\min_{f\in \mathcal{H},\; h} \left\{  \ell \left((x_{i}, y_{i}, \widetilde{f}(x_{i})) \,{,}\ldots{,}\, (x_{m}, y_{m}, \widetilde{f}(x_{m}))\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>admits a **representation** of the form
>$$
> \widetilde{f}(x) = \sum_{i=1}^{m}\alpha_{i} K(x_{i}, x) + \sum_{p=1}^{M}\beta_{p}\,\psi_{p}(x).
>$$
>with $\beta_{p}\in \mathbb{R}$ for all $p\in [M]$.

- [[Linear Span over a Set of Vectors]]


## Explanation


## Example






-----------
##  Recommended Notes and References


- [[Regularized Loss Minimization]]
- [[Structural Risk Minimization]]

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]
- [[Support Vector Machine Linear Separable Case]]


- [[Kernel Methods in Machine Learning by Hofmann]] pp 16
- [[Learning with Kernels by Schölkopf]] pp 89, 91

- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 179 - 189
- [[Foundations of Machine Learning by Mohri]] pp 117
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 692