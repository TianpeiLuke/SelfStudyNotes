---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning/theory
keywords:
  - reproducing_kernel_hilbert_space
  - gaussian_process
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_theory
name: Reproducing Kernel Hilbert Space of Gaussian Process
date of note: 2024-06-03
---

## Concept Definition

>[!important]
>**Name**: Reproducing Kernel Hilbert Space of Gaussian Process

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $(X_{t}, t\in T)$ be a *centered Gaussian process* with distribution $\mathcal{N}$. 
>
>Denote $F$ as the *linear span* of the collection of Gaussian random variables
>$$
>F = \text{span}\left\{ X_{t}, t\in T \right\} \subset L^2(\Omega, \mathscr{F}, \mathcal{P})
>$$ 
>
>Then **the reproducing kernel Hilbert space** $\mathcal{H}$ of **Gaussian process** is *isometric* to the *closure* of $F$ in $L^2(\Omega, \mathscr{F}, \mathcal{P})$.
>
>Specifically, it is the *Hilbert space* $\mathcal{H}$ of functions
>$$
>t \mapsto \mathbb{E}_{ \mathcal{N} }\left[ h\,X \right](t) :=  \mathbb{E}_{ \mathcal{N} }\left[ h\,X(t) \right]
>$$
>for all $h \in \overline{F} \subset L^2(\Omega, \mathscr{F}, \mathcal{P}),$ with *inner product*
>$$
>\left\langle\; \mathbb{E}_{ \mathcal{N} }\left[ h_{1}\,X \right] \,,\,  \mathbb{E}_{\mathcal{N}}\left[ h_{2}\,X \right] \;  \right\rangle_{\mathcal{H}} :=  \mathbb{E}_{ \mathcal{N} }\left[ h_{1}\,h_{2} \right], \quad \forall h_{1}, h_{2} \in \overline{F}.
>$$

- [[Gaussian Process]]
- [[Reproducing Kernel Hilbert Space]]
- [[Hilbert Space]]
- [[Linear Span over a Set of Vectors]]
- [[Isometry and Isometric isomorphism]]


>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable space and $\mathcal{X} \subset \mathbb{C}^T$ be a *Banach space*. Let $X: \Omega \to \mathcal{X}$ be a $\mathcal{X}$-valued *centered Gaussian function* with distribution $\mathcal{N}$. 
>
>Denote $F$ as the space of all $\mathcal{N}$-*measurable linear functionals* evaluated at $X$
>$$
>F = \left\{ f(X): f\in X^{*} \right\} \subset L^2(\Omega, \mathscr{F}, \mathcal{N})
>$$ 
>
>Then **the reproducing kernel Hilbert space** $\mathcal{H}_{\mathcal{N}}$ of **Gaussian function** $X$ is defined as
>$$
>\mathcal{H}_{\mathcal{N}} := \left\{   \mathbb{E}_{ \mathcal{N} }\left[ h\,X \right]:\; \forall h \in \overline{F} \subset L^2(\Omega, \mathscr{F}, \mathcal{N})\right\}
>$$
>with *inner product*
>$$
>\left\langle\; \mathbb{E}_{ \mathcal{N} }\left[ h_{1}\,X \right] \,,\,  \mathbb{E}_{\mathcal{N}}\left[ h_{2}\,X \right] \;  \right\rangle_{\mathcal{H}_{\mathcal{N}}} :=  \mathbb{E}_{ \mathcal{N} }\left[ h_{1}\,h_{2} \right], \quad \forall h_{1}, h_{2} \in \overline{F}.
>$$


## Explanation

>[!info]
>For any $h\in \overline{F}$, then
>$$
>h = \sum_{i=1}^{n}a_{i}\;X(t_{i})
>$$
>for some $n \in \mathbb{N}$ and $(t_{1} \,{,}\ldots{,}\, t_{n}) \subset T$ and some $(a_{1} \,{,}\ldots{,}\, a_{n}) \in \mathbb{R}^n.$

>[!info]
>The *function* in RKHS $\mathcal{H}$ of Gaussian process  $(X_{t}, t\in T)$ is defined as
>$$
>f := \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{i=1}^{n}a_{i}\;X(t_{i})\right)  X(\cdot) \right] = \sum_{i=1}^{n}a_{i}\;K(t_{i}, \cdot).
>$$
>where
>$$
>K(t, s) =  \mathbb{E}_{ \mathcal{N} }\left[X(t)\,X(s)  \right]
>$$
>is the **covariance function** of Gaussian process, which is also a **reproducing kernel**.

- [[Covariance Function of Gaussian Process]]
- [[Reproducing Kernel of RKHS]]


>[!info]
>We see that
>$$
>I_{X}: f \to f(X)
>$$
>is a linear functional on $\mathcal{X}_{\mathcal{N}}^*$, the space of all $\mathcal{N}$-measurable linear functionals on $\mathcal{X}$.
>
>Thus
>$$
> \overline{F} := \overline{I_{X}(\mathcal{X}_{\mathcal{N}}^*)} \subset \mathcal{X}.
>$$

- [[Evaluation Functional]]
- [[RKHS of Gaussian Random Function]]




-----------
##  Recommended Notes and References

- [[RKHS of Gaussian Random Function]]
- [[Reproducing Kernel Hilbert Space]]
- [[Lp Space]]

- [[Gaussian Process]]


- [[Lectures on Gaussian Processes by Lifshits]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
