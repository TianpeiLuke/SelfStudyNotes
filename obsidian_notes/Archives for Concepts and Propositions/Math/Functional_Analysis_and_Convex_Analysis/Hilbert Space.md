---
tags:
  - concept
  - math/functional_analysis
keywords:
  - hilbert_space
topics:
  - functional_analysis
name: Hilbert space
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Hilbert Space


>[!important] Definition
>A **complete** **inner product** space is called a **Hilbert space**. 

- [[Inner Product Space]]
- [[Complete Metric Space]]

## Examples

>[!example]
>A **finite-dimensional** *inner product space* $(V, \left\langle  \cdot\,,\, \cdot   \right\rangle)$ is a **Hilbert space**.
>
>This includes $\mathbb{R}^n$ and $\mathbb{C}^n$.

>[!example]
>The space of all **square-summable sequences** $$\ell^2 := \left\{ (a_{0}, a_{1} \,{,}\ldots{,}\,): \; a_{i} \in \mathbb{C},  \sum_{n=1}^{\infty}a_{n}^2 \le \infty  \right\} \subset \mathbb{C}^{\infty} $$ is a *Hilbert space* with respect to inner product
>$$
>\left\langle  a\,,\,b   \right\rangle_{\ell^2} := \sum_{n=1}^{\infty}a_{n}\bar{b}_{n}
>$$

- [[omega Tuples]]

>[!example]
>The space of all **square integrable functions** $$L^2(\mathcal{X},\mu) := \left\{f \in \mathbb{R}^{\mathcal{X}}:\; \int_{\mathcal{X}}|f|^2 \,d\mu < \infty \right\} $$ is a *Hilbert space* with respect to inner product
>$$
>\left\langle  f\,,\,g    \right\rangle_{L^2} := \int_{\mathcal{X}}\,f\,\bar{g}\,d\mu
>$$
>where $\mathcal{X}$ is a *complex vector space*.

- [[Lp Space]]

>[!example]
>The space of all **random variables** with **finite second moments** $$L^2(\Omega, \mathcal{P}) := \left\{ X \in \mathbb{R}^{\Omega}: \mathbb{E}_{ \mathcal{P} }\left[  |X|^2 \right] < \infty \right\} $$
>is a *Hilbert space* with respect to inner product
>$$
>\left\langle  X\,,\,Y    \right\rangle_{L^2} := \mathbb{E}_{ \mathcal{P} }\left[  X\,Y \right]
>$$

- [[Expectation of Random Variable]]


## Banach Space

- [[Banach Space]]


## Complete Orthonormal Basis

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Gram-Schmidt Orthogonalization]]
- [[Coordinate Representation in Hilbert Space and Fourier Coefficients]]
- [[Separable Hilbert Space]]


## Orthogonal Projection

- [[Direct Sum of Hilbert Spaces]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[Projection Theorem of Hilbert Spaces]]
- [[Projection Operator in Hilbert Space]]


## Representation of Dual 

- [[Riesz Representation Theorem]]


## Self-Reflexive

- [[Reflexive Normed Space and Bidual of Normed Space]]

## Operator on Hilbert Space

- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Self-Adjoint Operator in Hilbert Space]]



-----------
##  Recommended Notes and References

- [[Inner Product Space]]
- [[Complete Metric Space]]

- [[Concepts and Theorems in Hilbert Space]]

- [[Banach Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)