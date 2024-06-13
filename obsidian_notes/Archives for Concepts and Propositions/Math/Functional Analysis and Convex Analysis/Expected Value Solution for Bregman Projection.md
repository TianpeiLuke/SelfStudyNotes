---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - bregman_divergence
  - variational_inference
topics:
  - information_theory
name: Expected Value Solution for Bregman Projection
date of note: 2024-05-07
---

## Theorem

>[!important]
>**Name**: Expected Value Solution for Bregman Projection


>[!important] Proposition
>Let $I \subseteq \mathbb{R}$ be an *open interval* and let $f: I \to \mathbb{R}$ be **convex** and **differentiable**. 
>
>For any $x,y \in I$, **the Bregman divergence** of $f$ from $x$ to $y$ is 
>$$\mathbb{D}_{f}\left(y  \left\|\right. x \right) := f(y) - f(x) - f'(x)(y-x).$$ 
>
>Let $X$ be an $I$-valued random variable. Then
>$$
> \begin{align}
> \mathbb{E}\left[ f(X) - f( \mathbb{E}\left[X\right]) \right] &= \inf_{a \in I}\mathbb{E}\left[f(X) - f(a) - f'(a)(X-a)\right]
> \end{align}
>$$ 

- [[Bregman Projection]]
- [[Bregman Divergence]]
- [[Convex Function]]

## Explanation


>[!info]
>The [[Variational Formula for Entropy Functional]] can be derived from the above formula. 


## Properties



-----------
##  Recommended Notes and References

- [[Variational Formula for Entropy Functional]]


- [[Bregman Projection]]
- [[Bregman Divergence]]
- [[Entropy Functional]]


- [[Legendre Transform]]

- [[Concentration Inequalities by Boucheron]]


