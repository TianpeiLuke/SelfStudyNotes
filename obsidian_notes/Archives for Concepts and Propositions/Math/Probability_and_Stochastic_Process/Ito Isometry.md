---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_isometry
topics:
  - stochastic_process
name: Itô Isometry
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Isometry

![[Ito Stochastic Integration#^ad88e0]]

- [[Ito Stochastic Integration]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

>[!important] Theorem (Itô Isometry)
>Let $X, \;Y\in \mathbb{L}^2[0,T]$ be *progressive measurable processes*, and $a, b\in \mathbb{R}$.
>
>Then
>  $$
>  \mathbb{E}\left[ \left(\int_{0}^{T} X_{t}\;dW \right)^2 \right] = \mathbb{E}\left[  \int_{0}^{T} X^2_{t}\;dt \right]
> $$
>and
> $$
>  \mathbb{E}\left[ \int_{0}^{T} X_{t}\;dW\;\int_{0}^{T} Y_{t}\;dW \right] = \mathbb{E}\left[  \int_{0}^{T} X_{t}\,Y_{t}\;dt \right]
> $$

## Explanation


## Isometry between Hilbert Space


>[!important]
>We can consider the **Itô stochastic integral** as a linear map $$I: \mathbb{L}^2[0,T] \to L^2(\Omega).$$
>
>Then $I$ is an **isometry** on *normed vector space* with respect to *norm* induced by the **inner product**
>$$
>\left\langle X , Y \right\rangle_{\mathbb{L}^2(0,T)} :=  \mathbb{E}\left[  \int_{0}^{T} X_{t}\,Y_{t}\;dt  \right] 
>$$
>and *inner product*
>$$
>\left\langle A , B \right\rangle_{L^2(\Omega)} =  \mathbb{E}\left[  A\,B\right].
>$$
>
>That is, the **Itô Isometry** can be written as  
>$$
> \left\langle I(X) \,,\, I(Y)  \right\rangle_{L^2(\Omega)} = \left\langle X , Y \right\rangle_{\mathbb{L}^2(0,T)}
>$$

- [[Isometry and Isometric isomorphism]]
- [[Inner Product Space]]
- [[Hilbert Space]]
- [[Progressively Measurable Stochastic Process]]
- Wikipedia [Ito_isometry](https://en.wikipedia.org/wiki/It%C3%B4_isometry)




-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Riemann–Stieltjes Integration]]
- [[Ito Stochastic Integration of Step Process]]


- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]