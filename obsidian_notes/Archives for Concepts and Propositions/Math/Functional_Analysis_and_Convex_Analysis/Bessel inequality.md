---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - bessel_inequality
topics:
  - functional_analysis
  - linear_algebra
name: Bessel's inequality
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Bessel's inequality


>[!important] Bessel's inequality
>Let $\{x_i\}_{i=1}^{n}$ be an **orthonormal set** in an *inner product space* $V$. Then for all $x \in V$,
>$$
> \begin{align*}
>  \lVert x \rVert^2 &\ge \sum_{i=1}^{n} \lvert \left\langle x_{i}\,,\,x    \right\rangle \rvert^2 
> \end{align*}
>$$
>The inequality holds only when $\{x_i\}_{i=1}^{n}$ be a **complete orthonormal set** in an *inner product space* $V$, i.e. they spans the entire space.

- [[Pythagorean Theorem and Parallelogram Law]]
- [[Cauchy-Schwartz Inequality]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Coordinate Representation in Hilbert Space and Fourier Coefficients]]

## Explanation

>[!info]
>$\left\langle  x_{i}\,,\, x   \right\rangle$ is the **projection vector** of $x$ along the basis axis of $x_{i}$. We can define the **projection vector** of $x$ on the linear subspace spanned by $\{x_i\}_{i=1}^{n}$ as 
>$$
>x_{\parallel} = [\left\langle  x_{1}\,,\, x  \right\rangle \; \,{,}\ldots{,}\,\; \left\langle  x_{n}\,,\, x   \right\rangle]
>$$
>
>Thus, the Bessel's inequality has a simple geometric interpretation: $$ \lVert x \rVert^2  \ge \lVert x_{\parallel} \rVert^2  $$ i.e. **the projection on linear subspace will shrink the length of a vector.** This is also the result of cosine inequality in basic Euclidean geometry.






-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Inner Product Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)