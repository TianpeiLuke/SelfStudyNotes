---
tags:
  - concept
  - math/functional_analysis
keywords:
  - coordinate_representation
  - fourier_coefficient
  - parseval_relation
topics:
  - functional_analysis
name: Coordinate System of Hilbert Space
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**:  Coordinate Representation in Hilbert Space

>[!important] Theorem
>Let $\mathcal{H}$ be a Hilbert space and $S = (x_{\alpha})_{\alpha \in A}$ an **orthonormal basis**. 
>
>Then for each $y \in \mathcal{H}$,
>$$
> \begin{align}
> y &= \sum_{\alpha \in A}\left\langle  y\,,\, x_{\alpha}   \right\rangle \; x_{\alpha} 
> \end{align}
>$$ 
> and
>$$ 
> \begin{align}
> \lVert y \rVert_{\mathcal{H}} &= \sum_{\alpha \in A}\lvert \left\langle  y\,,\, x_{\alpha}   \right\rangle \rvert^2 
> \end{align}
>$$ 
> The equality above means that the sum on the right-hand side *converges (independent of order) to* $y$ in $\mathcal{H}$. 

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Bessel inequality]]

>[!important] Theorem
>**Conversely**, if 
>$$
>\sum_{\alpha \in A}|c_{\alpha}|^2 < \infty, \quad c_{\alpha} \in \mathbb{C},
>$$   
>then $\sum_{\alpha \in A}c_{\alpha} x_{\alpha}$ converges to *an element* of $\mathcal{H}$.

>[!important] Definition
>Let $\mathcal{H}$ be a Hilbert space and $S = (x_{\alpha})_{\alpha \in A}$ an **orthonormal basis**. 
>
>For each $y\in \mathcal{H}$, the **Parseval's relation** is defined as 
>$$
> \begin{align}
> y &= \sum_{\alpha \in A}\left\langle  y\,,\, x_{\alpha}   \right\rangle \; x_{\alpha}. 
> \end{align}
>$$ 
>and the *coefficients* $$k_{\alpha} := \left\langle  y\,,\, x_{\alpha}    \right\rangle$$ is called the **Fourier coefficients** of $y$ with respect to the basis $x_{\alpha}.$

- [[Fourier Series and Fourier Transform]]

## Explanation





-----------
##  Recommended Notes and References

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Fourier Series and Fourier Transform]]

- [[Orthogonality in Inner Product Space]]
- [[Basis of Vector Space]]
- [[Hilbert Space]]