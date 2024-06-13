---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - spectral_radius
topics:
  - functional_analysis
  - linear_algebra
name: Spectral Radius of Linear Operator
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Radius of Linear Operator

>[!info]
>The **Neumann series** as below converges in norm when $\lVert T \rVert < 1,$ 
>$$
> \frac{1}{I - T} = \left(I +  \sum_{n=1}^{\infty} T^n \right).
>$$
>
>
>Thus, the resolvent has the following **Neumann series**
>$$
>R_{\lambda}(T) =  \frac{1}{\lambda} \frac{1}{I - T / \lambda}  = \frac{1}{\lambda} \left\{ I + \sum_{n=1}^{\infty}\left( \frac{T}{\lambda} \right)^n \right\}  
>$$
>where  the RHS converges in norm when $|\lambda| > \lVert T \rVert$.
>
>It follows that
>$$
>|\lambda| \to \infty \implies \lVert R_{\lambda}(T) \rVert \to 0.
>$$

- [[Resolvent Set and Spectrum of Linear Operator]]

>[!important] Definition
>Let $$r(T) := \sup\{ \lvert \lambda \rvert: \lambda \in \sigma(T)   \}$$
>
>$r(T)$ is called the **spectral radius** of $T$.

## Explanation


## Property

>[!important] Theorem
>Let $X$ be a *Banach space*, $T \in \mathcal{L}(X)$. 
>
>Then $\lVert T^n \rVert^{1/n}$ is a **convergent series** and 
>$$
>\lim_{ n \to \infty } \lVert T^n \rVert^{1/n} = r(T).
>$$  
>
>If, furthermore, $X$ is a *Hilbert space*, and $T$ is **self-adjoint**, then
>$$
>\lim_{ n \to \infty } \lVert T^n \rVert^{1/n} = r(T) = \lVert T \rVert. 
>$$

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Space of Bounded Linear Operators]]
- [[Hilbert Space]]
- [[Banach Space]]






-----------
##  Recommended Notes and References


- [[Resolvent Set and Spectrum of Linear Operator]]

- [[Space of Bounded Linear Operators]]
- [[Hilbert Space]]

- [[Eigenspace and Spectrum for Linear Map]]

- [[Functional Analysis by Reed]]