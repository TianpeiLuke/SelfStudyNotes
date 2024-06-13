---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - weak_derivative
  - derivative_tempered_distribution
  - sobolev_space
  - Lp_space
topics:
  - functional_analysis
  - topology
name: Sobolev Space
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Sobolev Space

![[Weak Derivative via Tempered Distribution#^13abe5]]

- [[Weak Derivative via Tempered Distribution]]

>[!important] Definition
>Let $1 \le p < +\infty$,  the **Sobolev space** $W^{k, p}(\Omega)$ is the space of all functions $f\in L^p(\Omega)$ such that 
>- $f$ and 
>- all of its *weak derivatives* $D^{\alpha}f$ for all $|\alpha| \le k$
>
>has *finite $L^p$ norm*. That is,
>$$
>W^{k, p}(\Omega) = \left\{ f\in L^p(\Omega): \lVert D^{\alpha}\,f \rVert_{L^p(\Omega)} < \infty, \;\; \forall |\alpha| \le k  \right\}. 
>$$
>
>The *Sobolev space* admits a natural **norm**
>$$
>\begin{align*}
>\lVert f \rVert_{W^{k, p}} := \left( \sum_{|\alpha| \le k} \left\lVert D^{\alpha}f \right\rVert_{L^p(\Omega)}^{p}    \right)^{1 / p} = \left( \sum_{|\alpha| \le k} \int_{\Omega}  \left\lvert D^{\alpha}f(x) \right\rvert^{p}  dx   \right)^{1 / p} < \infty.
>\end{align*}
>$$

- [[Weak Derivative via Tempered Distribution]]
- [[Lp Space]]
- [[Norm and Normed Space]]


>[!important] Definition
>For $p = \infty$, 
>$$
>\begin{align*}
>\lVert f \rVert_{W^{k, \infty}} :=  \max_{|\alpha| \le k}\; \left\lVert D^{\alpha}f \right\rVert_{L^{\infty}(\Omega)}.
>\end{align*}
>$$

>[!important] Definition
>We denote $$H^k(\Omega) := W^{k ,2}(\Omega)$$ as it is a **Hilbert space** with $\lVert \cdot \rVert_{W^{k, 2}}$.
>
>Note that $H^0(\Omega) = L^2(\Omega)$.



## Explanation



## Banach Space

>[!important] Proposition
>The **Sobolev space** $W^{k,p}(\Omega)$ is a **Banach space**.

- [[Banach Space]]







-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Banach Space]]
- [[Lp Space]]


- [[Weak Derivative via Tempered Distribution]]
- [[Space of Tempered Distributions]]
- [[Norm and Normed Space]]

- [[Vector Space over a Field]]
- [[Hölder Space]]


- [[Functional Analysis by Reed]]
- Wikipedia [Sobolev space](https://en.wikipedia.org/wiki/Sobolev_space)