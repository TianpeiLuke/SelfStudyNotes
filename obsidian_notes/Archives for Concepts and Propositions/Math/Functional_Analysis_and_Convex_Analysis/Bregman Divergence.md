---
tags:
  - concept
  - math/information_theory
  - math/functional_analysis
  - optimization/theory
  - optimization/algorithm
  - statistics/estimation
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
>The **Bregman divergence** associated with $f$ for points $x,y \in \mathcal{X}$  is defined as 
>$$
>\mathbb{D}_{f}\left( x \left\|\right. y\right) = f(x) - f(y) - \left\langle  \nabla f(y)\,,\,  x - y \right\rangle  
>$$

^b31c31


## Explanation


![[Geometric-interpretation-of-Bregman-Divergence.png]]

>[!important]
>The Bregman divergence is the *difference* between 
>- the value of $f$ at point $x$, i.e. $f(x)$ and 
>- the value of the **first-order Taylor expansion** of $f$ *around point* $y$ *evaluated* at point $x$, i.e. $$f(y) + \left\langle \nabla f(y) , x - y \right\rangle$$


- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Lie Derivative of Vector Field]]

## Properties


- [[Necessary and Sufficient Conditions for Convex Function]]

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

## KL Divergence within Exponential Family

![[Kullback-Leibler Divergence for Exponential Family#^a7c80d]]

- [[Kullback-Leibler Divergence for Exponential Family]]

## Bregman Divergence as Proximal Operator

- [[Generalized Proximal Method]]
- [[Bregman Divergence Minimization]]
- [[Majorization-Minimization Algorithm]]
- [[Mirror Descent Algorithm]]




-----------
##  Recommended Notes and References

- [[Divergence Function on Manifold]]

- Wikipedia [Bregman divergence](https://en.wikipedia.org/wiki/Bregman_divergence)
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]