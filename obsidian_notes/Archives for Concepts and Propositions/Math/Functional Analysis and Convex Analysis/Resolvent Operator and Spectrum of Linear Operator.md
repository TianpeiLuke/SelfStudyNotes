---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - resolvent_set_linear
  - spectrum_operator
  - resolvent
topics:
  - functional_analysis
  - linear_algebra
name: Resolvent Set of Linear Operator
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Resolvent Set of Linear Operator

>[!important] Definition
>Let $X$ be a *Hilbert space* and $T \in \mathcal{L}(X)$. 
>
>The **resolvent set** $\rho(T)$ of $T$ is the set of *complex numbers* $\lambda \in \mathbb{C}$ such that $\lambda I - T$ is a *bijection* with **bounded inverse**. That is,
>$$
>\rho(T) := \left\{ \lambda \in \mathbb{C}: (\lambda I - T)^{-1} \text{ exists and bounded}  \right\} 
>$$

- [[Hilbert Space]]
- [[Bijective Function and Inverse Function]]


>[!important] Definition
>The inverse operator
>$$
>R_{\lambda}(T) := (\lambda I - T)^{-1}
>$$
>is called the **resolvent** of $T$ *at* $\lambda$.

>[!important] Definition
>If $\lambda \not\in \rho(T)$, then $\lambda$ is said to be in the **spectrum** of $T$, denoted as $\sigma(T).$
>
>That is
>$$
>\sigma(T) := \mathbb{C} \setminus \rho(T) = \left\{ \lambda \in \mathbb{C}: (\lambda I - T) \text{ is not bijective or has unbounded inverse} \right\} 
>$$

- [[Eigenspace and Spectrum for Linear Map]]



## Explanation


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


-----------
##  Recommended Notes and References

- [[Bijective Function and Inverse Function]]

- [[Space of Bounded Linear Operators]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

- [[Eigenspace and Spectrum for Linear Map]]

- [[Functional Analysis by Reed]]