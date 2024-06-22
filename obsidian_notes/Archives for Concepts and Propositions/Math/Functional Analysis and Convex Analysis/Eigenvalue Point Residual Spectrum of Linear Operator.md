---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - spectrum_operator
  - eigen_value
  - point_spectrum
  - residual_spectrum
topics:
  - functional_analysis
  - linear_algebra
name: Eigenvalue Point Residual Spectrum of Linear Operator
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Eigenvalue Point Residual Spectrum of Linear Operator

>[!important] Definition
>Let $X$ be a *Hilbert space* and $T \in \mathcal{L}(X)$. 
>
>A complex value $\lambda \in \mathbb{C}$ is called an **eigenvalue** *of* $T$ if there exists a non-zero vector $x\in X$ such that 
>$$
>Tx = \lambda x.
>$$
>Such vector $x$ is called the **eigenvector** of $T$ *associated with* $\lambda$.

- [[Eigenvalue and Eigenvector for Linear Map]]

>[!important] 
>If $\lambda$ is an *eigenvalue* of $T$, the *resolvent* of $T$
>$$
>(\lambda I - T)
>$$
>is **not injective**. Thus $\lambda \in \sigma(T)$ is in the **spectrum** of $T$.

- [[Resolvent Operator and Spectrum of Linear Operator]]
- [[Hilbert Space]]
- [[Injective Function]]

>[!important] Definition
>The set of all *eigenvalues* of $T$ is called the **point spectrum** of $T$.

>[!impotrant]
>If $\lambda$ is *not an eigenvalue* and if 
>$$
>\text{Im}\left(\lambda I - T\right)
>$$
>is *not dense*, then $\lambda$ is said to be in the **residual spectrum** of $T$. 




## Explanation

>[!info]
>For finite dimensional $X$, the **point spectrum** is **all** of the *spectrum*.
- [[Eigenspace and Spectrum for Linear Map]]


## Nonempty 

>[!important] Corollary
>Let $X$ be a **Banach space**, $T \in \mathcal{L}(X)$. 
>
>Then the **spectrum** of $T$ is **not empty**.
>$$
>\sigma(T) \neq \emptyset.
>$$ 

>[!info]
>The resolvent has the following **Neumann series**
>$$
>R_{\lambda}(T) = \frac{1}{\lambda} \left\{ 1 + \sum_{n=1}^{\infty}\left( \frac{T}{\lambda} \right)^n \right\}  
>$$



-----------
##  Recommended Notes and References

- [[Bijective Function and Inverse Function]]

- [[Space of Bounded Linear Operators]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]

- [[Functional Analysis by Reed]]