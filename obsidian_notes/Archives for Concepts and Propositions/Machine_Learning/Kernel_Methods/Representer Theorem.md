---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/kernel_methods
  - representer_theorem
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
>f \in \arg\min_{f\in \mathcal{H}} \left\{  \ell \left((x_{1}, y_{1}, f(x_{1})) \,{,}\ldots{,}\, (x_{m}, y_{m}, f(x_{m}))\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>admits a **representation** of the form
>$$
> f(x) = \sum_{i=1}^{m}\alpha_{i} K(x_{i}, x).
>$$

^315388

- [[Regularized Loss Minimization]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Representation of Evaluation Functional in RKHS]]
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
>\widetilde{f}  \in \arg\min_{f\in \mathcal{H},\; h} \left\{  \ell \left((x_{1}, y_{1}, \widetilde{f}(x_{1})) \,{,}\ldots{,}\, (x_{m}, y_{m}, \widetilde{f}(x_{m}))\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>admits a **representation** of the form
>$$
> \widetilde{f}(x) = \sum_{i=1}^{m}\alpha_{i} K(x_{i}, x) + \sum_{p=1}^{M}\beta_{p}\,\psi_{p}(x).
>$$
>with $\beta_{p}\in \mathbb{R}$ for all $p\in [M]$.

- [[Linear Span over a Set of Vectors]]

### Distribution Risk Minimization

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space*, and $\mathscr{P}(\mathcal{X})$ is the *space of all probability measures* on $\mathcal{X}$. Denote $\mathcal{H}  \subset \mathcal{Y}^{\mathcal{X}}$ as the *reproducing kernel Hilbert space (RKHS)* of measurable functions over $\mathcal{X}$.
>
>Let assume that 
>- we have access to a training sample $$(\mathcal{P}_{1}, y_{1}) \,{,}\ldots{,}\, (\mathcal{P}_{n}, y_{n}) \in \mathscr{P}(\mathcal{X}) \times \mathcal{Y}$$ generated from some unknown distribution over $\mathscr{P}(\mathcal{X}) \times \mathcal{Y}$, 
>- a *strictly monotonically increasing function* $$\Omega: [0, \infty) \to \mathbb{R},$$ 
>- and a *loss function* $$\ell: (\mathscr{P}(\mathcal{X}) \times \mathcal{Y} \times \mathcal{Y}) \to \mathbb{R} \cup \{+\infty\},$$
>
>The **distributional risk minimization (DRM)**
>$$
>\min_{f\in \mathcal{H}} \left\{  \ell \left((\mathcal{P}_{1}, y_{1},  \mathbb{E}_{ \mathcal{P}_{1} }\left[ f \right]) \,{,}\ldots{,}\, (\mathcal{P}_{n}, y_{n}, \mathbb{E}_{ \mathcal{P}_{n} }\left[ f \right])\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>- The optimal solution has the form $$f(x) = \sum_{i=1}^{m}\alpha_{i}\;  \mathbb{E}_{ \mathcal{P}_{i} }\left[ K(X, x) \right] = \sum_{i=1}^{m}\alpha_{i}\;\mu_{\mathcal{P}_{i}}$$ where $\mu_{\mathcal{P}_{i}}$ is the *kernel mean embedding* of $\mathcal{P}_{i}$ $$\mu_{\mathcal{P}_{i}} =  \mathbb{E}_{ \mathcal{P}_{i} }\left[K(X, \cdot)  \right]$$


- [[Kernel Mean Embedding of Distribution]]
- [[Space of Bounded Signed Measures]]
- [[Measure Space and Countably Additive Measure]]


![[distributional_data_kernel_embedding.png]]


>[!important] Representer Theorem (Distributional Case)
>Let $(\mathcal{X}, \mathscr{F})$ be a measureable space, and  $\mathcal{H} \subset \mathbb{R}^{\mathcal{X}}$ be a *reproducing kernel Hilbert space* of *measurable real-valued function*. Denote 
>- by $\Omega : [0, \infty) \to \mathbb{R}$ a **strictly monotonic increasing function**, and 
>- by  $\mathscr{P}(\mathcal{X})$ the *space of all probability measures* on $\mathcal{X}$.
>- by $\ell : (\mathscr{P}(\mathcal{X}) \times \mathbb{R}^2)^m  \to \mathbb{R} \cup \{\infty\}$ an arbitrary *loss function*. 
>  
>Then each **minimizer** $f\in \mathcal{H}$ of the **regularized risk** 
>$$
>f \in \arg\min_{f\in \mathcal{H}} \left\{  \ell \left((\mathcal{P}_{1}, y_{1},  \mathbb{E}_{ \mathcal{P}_{1} }\left[f\right]) \,{,}\ldots{,}\, (\mathcal{P}_{m}, y_{m}, \mathbb{E}_{ \mathcal{P}_{m} }\left[f\right])\right) + \Omega \left(\lVert f \rVert_{\mathcal{H}} \right) \right\}
>$$
>admits a **representation** of the form
>$$
> f(x) = \sum_{i=1}^{m}\alpha_{i}\;\mathbb{E}_{ X\sim\mathcal{P}_{i} }\left[  K(X, x) \right]  = \sum_{i=1}^{m}\alpha_{i}\;\mu_{\mathcal{P}_{i}}.
>$$
>where $\mu_{\mathcal{P}_{i}}$ is the *kernel mean embedding* of $\mathcal{P}_{i}$ $$\mu_{\mathcal{P}_{i}} =  \mathbb{E}_{ \mathcal{P}_{i} }\left[K(X, \cdot)  \right]$$

## Explanation

>[!info]
>**Monotonicity** of $\Omega$ is **necessary** to ensure that the theorem holds. 
>- It does not prevent the *regularized risk functional* from having *multiple local minima*. 
>- To ensure a single minimum, we would need to require **convexity**.
>- If we discard the **strictness** of the *monotonicity*, then it no longer follows that each **minimizer** of the *regularized risk* admits an **expansion**; 
>- it still follows, however, that there is **always another solution** that is **as good**, and that does **admit the expansion**.

>[!important]
>The **significance** of the **Representer Theorem** is that although we might be trying to solve an *optimization problem* in an **infinite-dimensional space** $\mathcal{H}$, containing *linear combinations of kernels* centered on *arbitrary points* of $X$, it states that the solution lies in the **span** of $m$ **particular kernels** --  those centered on the training points.
> 
> In the **Support Vector** community,
> $$
> \begin{align*}
> f(x) &= \sum_{n=1}^{m}\alpha_n K(x_n, x)
> \end{align*}
>$$  
>is called the **Support Vector expansion**. 
>- For suitable choices of loss functions, it has empirically been found that many of the $\alpha_n$ often equal $0$.
> 

- [[Support Vector Machine Kernel Expansion and RKHS]]


## Example






-----------
##  Recommended Notes and References


- [[Regularized Loss Minimization]]
- [[Structural Risk Minimization]]

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]
- [[Support Vector Machine Linear Separable Case]]


- [[Kernel Methods in Machine Learning by Hofmann]] pp 16 - 19
- [[Learning with Kernels by Schölkopf]] pp 89, 91
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 57 - 59
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 179 - 189
- [[Foundations of Machine Learning by Mohri]] pp 117
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 692

