---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - gaussian_function
  - karhunen_loeve_expansion
topics:
  - probability
  - stochastic_process
name: Gaussian Random Function in Hilbert Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Karhunen-Loève Expansion of Gaussian Random Function in Hilbert Space

- [[Gaussian Random Function]]

>[!info]
>Let $\mathcal{H}$ be a **separable Hilbert space** whose inner product will be denoted by $\left\langle \cdot , \cdot \right\rangle_{\mathcal{H}}$. By the *Riesz representation* theorem, we can identify its *dual space* $\mathcal{H}^{*}$ with $\mathcal{H}$, i.e. for each $f \in \mathcal{H}^{*}$, there exists a *unique* $x_f \in \mathcal{H}$ such that
>$$
> \begin{align*}
> \left\langle f , x \right\rangle = f(x) &= \left\langle x , x_{f} \right\rangle_{\mathcal{H}}, \quad \forall x \in \mathcal{H}.
> \end{align*} 
>$$ 
>Define $h: \mathcal{H}^{*} \rightarrow \mathcal{H}$ as an **isometric isomorphism** that maps $f \mapsto x_f$.

- [[Separable Space]]
- [[Hilbert Space]]

### Construction of Gaussian Element in Hilbert Space

>[!important] Construction of Gaussian Element in Hilbert Space
>In order to construct a Gaussian element in $\mathcal{H}$, consider
>- a **complete orthonormal basis** $\{\varphi_n\}_{n=1}^{\infty}$ on $\mathcal{H}$, 
>- a  sequence of *independent* $\mathcal{N}(0, 1)$-distributed random variables $\{\xi_n\}_{n=1}^{\infty}$, and 
>- a sequence of *non-negative numbers* $\{\sigma_n\}_{n=1}^{\infty}$ satisfying assumption $$\sum_{n=1}^{\infty}\sigma_n^2 < \infty$$ 
>
>so that the series
>$$
> \begin{align*}
> \sum_{n=1}^{\infty}\sigma_n  \xi_n(\omega) \varphi_n
> \end{align*}
>$$ 
 >is **convergent** in **$\lVert \cdot \rVert_{\mathcal{H}}$-norm** **almost surely** in $\mathcal{H}$.

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Gaussian Random Variable]]
- [[Convergence in Norm]]
- [[Pointwise Almost Everywhere Convergence]]


 >[!important] Definition
>Let $\mathcal{H}$ be a **separable Hilbert space**.  Define a *random element* $X: \Omega \to \mathcal{H}$ as the *limit* of the series
>$$ 
> \begin{align}
> X=   \sum_{n=1}^{\infty}\sigma_n \xi_n \varphi_n
> \end{align} 
>$$ 
>where
>- $\{\varphi_n\}_{n=1}^{\infty}$ is a *complete orthonormal basis*  on $\mathcal{H}$, 
>- $\{\xi_n\}_{n=1}^{\infty}$ is a sequence of *independent* $\mathcal{N}(0, 1)$-distributed random variables, and 
>- $\{\sigma_n\}_{n=1}^{\infty}$ is a sequence of *non-negative numbers* satisfying assumption $$\sum_{n=1}^{\infty}\sigma_n^2 < \infty$$ 
>
>Then $X$ is a *Gaussian random element* in $\mathcal{H}$. 
>
>This *representation* is called the **Karhunen-Loève expansion** of Gaussian element in separable Hilbert space.

^3e7bb2

## Reproducing Kernel Hilbert Space

- [[Reproducing Kernel Hilbert Space]]
- [[RKHS of Gaussian Random Function]]
- [[RKHS of Gaussian Random Function in Hilbert Space]]



-----------
##  Recommended Notes and References

- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]
- [[Gaussian Random Function]]