---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - bobkov_inequality
topics:
  - concentration_inequality
name: Bobkov Inequality
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Bobkov's Inequality

![[Gaussian Isoperimetric Function#^fcd238]]


>[!important] Bobkov's Inequality (Rademacher Variable, or Binary Cube)
>Suppose $Z$ is **uniformly distributed over $\set{-1,1}^n$**. 
>
>Then for all $n \ge 1$ and for *all functions* $f: \set{-1, 1}^n \to [0,1]$,
>$$
> \begin{align}
> \gamma \left(  \mathbb{E}_{Z}\left[f(Z)\right] \right) &\le  \mathbb{E}_{Z}\left[ \sqrt{\gamma(f(Z))^2 + \lVert \nabla f(Z) \rVert_{2}^2 } \right]  
> \end{align}
>$$ 
>where $\gamma(x) = \varphi(\Phi^{-1}(x))$ is the **Gaussian isopermetric function**, and the gradient of function on binary cube is 
>$$
>\lVert \nabla f(Z)  \rVert_{2}^2 = \frac{1}{4}\left\lvert f(Z) - f(Z') \right\rvert^2
>$$

^48244d

- [[Gaussian Isoperimetric Function]]


>[!important] Bobkov's Inequality (Standard Gaussian Variable)
>Let $$Z := (Z_1 \,{,}\ldots{,}\, Z_n)$$ be a vector of **independent standard Gaussian** random variables. Let $f: \mathbb{R}^n \to [0, 1]$ be a *differentiable* function with gradient $\nabla f$.
>
>Then,
>$$
> \begin{align}
> \gamma \left(  \mathbb{E}_{Z}\left[f(Z)\right] \right) &\le  \mathbb{E}_{Z}\left[ \sqrt{\gamma(f(Z))^2 + \lVert \nabla f(Z) \rVert_{2}^2 } \right]  
> \end{align}
>$$ 
>where $\gamma(x) = \varphi(\Phi^{-1}(x))$ is the **Gaussian isopermetric function**.

^74be32


- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]


## Explanation





-----------
##  Recommended Notes and References

- [[Gaussian Isoperimetric Function]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Gaussian Isoperimetric Theorem]]
- [[Gaussian Concentration Theorem]]



- [[Concentration Inequalities by Boucheron]]