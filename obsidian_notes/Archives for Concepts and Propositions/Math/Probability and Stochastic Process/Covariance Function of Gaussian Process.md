---
tags:
  - concept
  - math/probability
  - math/stochastic_process
  - math/functional_analysis
keywords:
  - covariance_function
topics:
  - probability
  - stochastic_process
  - functional_analysis
name: Covariance Function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Covariance Function of Gaussian Process

![[Covariance Operator#^fb0b17]]

- [[Covariance Operator]]

>[!important] Definition
>Let $T$ be a *compact metric space* and $(X_{t}, t\in T)$ be a *zero-mean Gaussian process* indexed by $T$.
>
>The **covariance function** $K: T \times T \to \mathbb{R}$ is defined as
>$$
>K(s, t) := \mathbb{E}\left[  X(s)\,X(t) \right], \quad \forall t, s\in T.
>$$ 

- [[Gaussian Process]]
- [[Random Element and Random Variable]]
- [[Covariance Operator]]


## Explanation


## Covariance Operator 

>[!important]
>The Gaussian process is a *Gaussian random function* $$X: \Omega \to \mathcal{X} \subset \mathbb{C}^{T}.$$ Suppose $\widehat{K}: \mathcal{X}^{*} \to \mathcal{X}$ is the **covariance operator**.
>
>Let $\delta_{t}$ be the evaluation functional on $\mathcal{X}$ so that $$\left\langle  \delta_{t}\,,\, X(\omega)   \right\rangle = \delta_{t}(X(\omega))= X_{t}(\omega).$$
>where $\left\langle  \,,\,    \right\rangle$ is the [[Canonical Dual Pairing]].
>
>Thus the **covariance function** $K$ can be obtained via *the covariance operator*
>$$
>\begin{align*}
>K(s, t) &=  \mathbb{E}\left[  X(s)\,X(t) \right] \\
>&= \mathbb{E}\left[ \left\langle  \delta_{s}\,,\, X   \right\rangle  \,\left\langle  \delta_{t}\,,\, X   \right\rangle \right] \\
>&=  \left\langle   \delta_{s}\,,\,\widehat{K} \delta_{t}   \right\rangle
\end{align*}
>$$
>In other word
>$$
>(\widehat{K} \delta_{t})(s) = K(s, t)
>$$
>and
>$$
>(\widehat{K}g)(s) = \int K(s, t)\, d\mu_{g}(t)
>$$

- [[Evaluation Functional]]
- [[Covariance Operator]]

>[!example]
>Let $\mathcal{X}= \mathcal{C}(T)$ where $T$ is a **compact metric space**. By [[Riesz-Markov Representation Theorem]], the dual $\mathcal{X}^{*}= \mathcal{M}_{+}$ be space of *positive Radon measures* on $T$.
>
>Thus the **covariance operator** $\widehat{K}: \mathcal{X}^{*}\to \mathcal{X}$ can be obtained from **covariance function** $K(s, t)$ as
>$$
>\left\langle  f\,,\,\widehat{K}\,g  \right\rangle = \int_{T}\int_{T}K(s,t)d\mu_{f}(s)\,d\mu_{g}(t)
>$$
>or
>$$
>(\widehat{K}g)(s) = \int_{T}K(s,t)d\mu_{g}(t)
>$$
>where $g \mapsto \mu_{g}$ is an **isomorphism** by [[Riesz-Markov Representation Theorem]].


## Reproducing Kernel


>[!important]
>The covariance function $K$ is a **bilinear form**
>- **self-adjoint** $$K(s, t) = K(t, s)$$
>- **non-negative definite** function $$K(s,t) \ge 0, \quad \forall s, t \in T.$$

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Positive Semidefinite Operator]]

>[!important]
>The **covariance function** $K: T \times T\to \mathbb{R}$ is a **reproducing kernel**.

- [[Reproducing Kernel of RKHS]]


## Integral Kernel of Stochastic PDE






-----------
##  Recommended Notes and References

- [[Banach Space]]
- [[Random Element and Random Variable]]


