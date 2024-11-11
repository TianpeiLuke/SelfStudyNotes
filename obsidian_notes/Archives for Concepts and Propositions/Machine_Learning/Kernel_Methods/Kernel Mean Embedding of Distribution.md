---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - machine_learning/kernel_methods
  - machine_learning/density_estimation
keywords:
  - kernel_mean_embedding_distribution
topics:
  - kernel_methods
  - machine_learning/density_estimation
  - information_theory
  - information_geometry
name: Kernel Mean Embedding of Distribution
date of note: 2024-11-08
---

## Concept Definition

>[!important]
>**Name**: Kernel Mean Embedding of Distribution

>[!important] Definition  (Complete Orthonormal Basis Version)
>Let $(\mathcal{X}, \mathscr{F}, P)$ be a probability space and  $\mathcal{H}$ be a *reproducing Kernel Hilbert space (RKHS)* of functions with kernel $K$, indexed by $\mathcal{X}$.
>
>Let $\Phi := \{ \phi_{i} \}_{i=1}^{\infty}$  be a set of *complete orthonormal basis* in $\mathcal{H}$, $$\forall f \in \mathcal{H} \implies f(x) = \sum_{i=1}^{\infty}f_{i}\,\phi_{i}(x)$$ for some $\hat{f} := \{ f_{i} \}_{i=1}^{\infty} \subset \ell_{2}$.
>
>
>The **kernel mean embedding** of *distribution* $P$ is defined as 
>$$
>\begin{align*}
>\mu_{P} &:=  \left( \int_{\mathcal{X}}\phi_{i}\,dP\right)_{i=1}^{\infty} \\[8pt] 
>&:= \left( \mathbb{E}_{ P }\left[  \phi_{i}(X) \right]\right)_{i=1}^{\infty} \\[8pt] 
>&:= \mathbb{E}_{ P }\left[  \Phi(X) \right]
>\end{align*}
>$$
>- With kernel mean embedding $\mu_{P}$, the expectation of $f$ with respect to $P$ can be represented as the *inner product* in $\ell_{2}$ $$\mathbb{E}_{ P }\left[  f(X) \right] = \sum_{i=1}^{\infty}f_{i}\,\mathbb{E}_{ P }\left[  \phi_{i}(X) \right] = \left\langle  \hat{f}\,,\, \mu_{P}  \right\rangle_{\ell_{2}}$$

^300ada


- [[Probability Space]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[lp Sequence Space]]

>[!important] Definition (Kernel Version)
>Let $(\mathcal{X}, \mathscr{F}, P)$ be a probability space and  $\mathcal{H}$ be a *reproducing Kernel Hilbert space (RKHS)* of functions with kernel $K$, indexed by $\mathcal{X}$.
>- Note that $$\forall f\in \mathcal{H}  \implies f(x) = \left\langle  f\,,\,K(x ,\cdot)    \right\rangle_{\mathcal{H}}.$$
>
>The **kernel mean embedding** of *distribution* $P$ can be defined in terms of reproducing kernel $K$ as
>$$
>\begin{align*}
>\mu_{P} &:= \mathbb{E}_{ P }\left[  K(X, \cdot)\right] := \int_{\mathcal{X}}K(x, \cdot)\,dP(x)
>\end{align*}
>$$
>- Under this definition, the *kernel mean embedding* $\mu_{P} \in \mathcal{H}$ is a *function* on $\mathcal{X}$. 
>- And $$\mathbb{E}_{ P }\left[  f(X) \right] = \left\langle  f\,,\, \mu_{P}   \right\rangle_{\mathcal{H}}$$

^19844b

![[kernel_mean_embedding.png]]

### Empirical Kernel Mean Embedding

>[!important] Definition
>Let $\{ X_{i} \}_{i=1}^{n}$ be i.i.d. samples in $\mathcal{X}$ from $P$ and  $\mathcal{H}$ be a *reproducing Kernel Hilbert space (RKHS)* of functions with kernel $K$, indexed by $\mathcal{X}$. 
>
>The **empirical kernel mean embedding** is given by 
>$$
>\mu \left(P_{n}\right) := \frac{1}{n} \sum_{i=1}^{n}\, K(X_{i}, \cdot)
>$$
>or 
>$$
>\mu \left(P_{n}\right) := \frac{1}{n} \sum_{i=1}^{n}\, \Phi(X_{i}) = \left(  \frac{1}{n} \sum_{i=1}^{n}\,\phi_{k}(X_{i})\right)_{k=1}^{\infty} 
>$$
>where $$P_{n} = \frac{1}{n}\sum_{i=1}^{n}\delta_{X_{i}}$$ is the *empirical measure.*

^6e1506

- [[Empirical Process and Empirical Measure]]
- [[Empirical Risk Minimization]]

## Explanation

>[!important]
>It is called *embedding* since it is a **smooth embedding** from the *space of probability measures (functional space)* $P$ into $\ell_{2}$ space $$\mu_{\cdot}: \mathscr{P}(\mathcal{X}) \xhookrightarrow{} \ell_{2}\; \quad \mu_{P} :=\mu(P) \in \ell_{2}$$
>- This space of measures is a subspace of *dual of RKHS*. $$\mathscr{P}(\mathcal{X}) \subset \mathcal{H}^{*} \simeq \ell_{2}.$$
>  
>  
>Using the second definition, then the *kernel mean embedding*  is a **smooth embedding** from the *space of probability measures (functional space)* $\mathscr{P}$ into $\mathcal{H}$ space $$\mu_{\cdot}: \mathscr{P}(\mathcal{X}) \xhookrightarrow{} \mathcal{H}\; \quad \mu_{P} :=\mu(P) \in \mathcal{H}$$
>- This is equivalent to above, since for RKHS $$\mathcal{H} \simeq \mathcal{H}^{*} \simeq \ell_{2}$$

- [[Smooth Embedding]]
- [[Radon Measure]]
- [[Space of Bounded Signed Measures]]
- [[Riesz-Markov Representation Theorem]]
- [[Riesz Representation Theorem]]


## Maximum Mean Discrepancy

![[Maximum Mean Discrepancy between Probability Measures via RKHS#^345e1a]]

- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Integral Probability Metric between Probability Measures]]

## Kernel Density Estimation

>[!important]
>The **empirical kernel mean embedding** is equivalent to the **Parzen kernel density estimation**
>$$
>\mu \left(P_{n}\right)(x) := \frac{1}{n} \sum_{i=1}^{n}\, K(X_{i}, x) = \frac{1}{nh}\sum_{i=1}^{n}\,K\left( \frac{X_{i} - x }{h}\right)
>$$
>where the RKHS uses the *stationary kernel* $$K(x, y) := \frac{1}{h}K\left(\frac{x - y}{h}\right)$$

- [[Parzen Kernel Density Estimation]]

## Kernel Mean Embedding for Conditional Distribution

- [[Kernel Mean Embedding of Conditional Distribution]]



-----------
##  Recommended Notes and References



- [[Measure Space and Countably Additive Measure]]
- [[RKHS of Gaussian Process]]
- [[RKHS of Gaussian Random Function]]
- [[RKHS of Gaussian Random Function in Hilbert Space]]
- [[Gaussian Process]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 58 - 59,  891
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 22 - 64
- Wikipedia [Kernel_embedding_of_distributions](https://en.wikipedia.org/wiki/Kernel_embedding_of_distributions)