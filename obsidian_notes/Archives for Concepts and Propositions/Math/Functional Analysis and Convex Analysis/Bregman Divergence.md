---
tags:
  - concept
  - math/information_theory
  - math/functional_analysis
keywords:
  - bregman_divergence
topics:
  - information_theory
  - functional_analysis
name: Bregman Divergence
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Bregman Divergence

>[!important] Definition
>Let $f: \mathcal{X} \to \mathbb{R}$ be a *continuous differentiable* and *strictly convex* function defined on a *convex set* $\mathcal{X}$
>
>The **Bregman divergence** associated with $f$ for points $\boldsymbol{x}, \boldsymbol{y} \in \mathcal{X}$  is defined as 
>$$
>\mathbb{D}_{f}\left( \boldsymbol{x} \left\|\right. \boldsymbol{y}\right) = f(\boldsymbol{x}) - f(\boldsymbol{y}) - \left\langle  \nabla f(\boldsymbol{y})\,,\,  \boldsymbol{x} - \boldsymbol{y} \right\rangle  
>$$



>[!info]
>The Bregman divergence is the *difference* between the value of $f$ at point $\boldsymbol{x}$ and the value of the *first-order Taylor expansion* of $f$ around point $\boldsymbol{y}$ evaluated at point $x$:

## Explanation



## Properties


>[!important]
>For $\boldsymbol{x}$, $\boldsymbol{y}$ and $\boldsymbol{z}$, the **Pythagorean Theorem** holds
>$$\begin{align*}
>\mathbb{D}_{f}\left( \boldsymbol{x} \left\|\right. \boldsymbol{z}\right) + \mathbb{D}_{f}\left( \boldsymbol{y} \left\|\right. \boldsymbol{z}\right) &= \mathbb{D}_{f}\left( \boldsymbol{x} \left\|\right. \frac{\boldsymbol{x} + \boldsymbol{y}}{2}\right) + \mathbb{D}_{f}\left( \boldsymbol{y} \left\|\right. \frac{\boldsymbol{x} + \boldsymbol{y}}{2}\right)\\
>&\quad + 2 \mathbb{D}_{f}\left( \frac{\boldsymbol{x} + \boldsymbol{y}}{2} \left\|\right. \boldsymbol{z} \right)
\end{align*}
>$$


>[!important] Generalized Pythagorean Theorem
>For any $x \in \mathcal{X}$,  $a \in W$.
>$$
>\mathbb{D}_{f}\left(  a \left\|\right. x \right) \ge \mathbb{D}_{f}\left(  a \left\|\right. P_{W}(x) \right) + \mathbb{D}_{f}\left(  P_{W}(x) \left\|\right. x \right)
>$$ 
>where $P_{W}$ be **the Bregman projection** onto $W$,
>$$
>P_{W}(x) = \arg\min_{w \in W}\mathbb{D}_{f}\left( w \left\|\right. x \right).
>$$
>
>The equality holds if $P_{W}(x)$ in the *relative interior* of $W$.

>[!info]
>If $W$ is an affine space, then the equality always holds.

- [[Bregman Projection]]


## Solution for Bregman Projection

- [[Expected Value Solution for Bregman Projection]]



-----------
##  Recommended Notes and References

- [[Divergence on Manifold]]

- Wikipedia [Bregman divergence](https://en.wikipedia.org/wiki/Bregman_divergence)
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]