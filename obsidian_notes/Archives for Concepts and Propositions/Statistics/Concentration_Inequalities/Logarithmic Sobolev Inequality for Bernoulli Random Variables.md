---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - log_sobolev_inequality
topics:
  - concentration_inequality
  - information_theory
name: Logarithmic Sobolev Inequality for Rademacher Random Variables
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Logarithmic Sobolev Inequality for Bernoulli Random Variables

>[!important] Definition 
>The **Jackknife estimate of variance** of $f(X)$  is defined as
>$$
>\mathcal{E}(f) := \frac{1}{2}\mathbb{E}\left[ \sum_{i=1}^{n} \left(f(X) - f(\widetilde{X}^{(i)}) \right)^2 \right]
>$$
>where $X := (X_{1} \,{,}\ldots{,}\, X_{n})$ and $$\widetilde{X}^{(i)} := \left(X_{1} \,{,}\ldots{,}\, X_{i-1}, X_{i}^{'}, X_{i+1} \,{,}\ldots{,}\, X_{n}\right)$$
>is obtained by **replacing** $i$-th component of $X$ by an *independent copy* $X_{i}^{'}$.


>[!important] Proposition (Logarithmic Sobolev Inequality for Rademacher Random Variables)
>If $f: \set{-1, +1}^n \to \mathbb{R}$ be an arbitrary real-valued function  defined on the **$n$-dimensional binary hypercube** and assume that $X$ is **uniformly distributed over $\set{-1, +1}^n$**. Then
>$$
> \begin{align}
> \text{Ent}(f^2) &\le 2  \mathcal{E}(f) 
> \end{align}
>$$ 
>or
>$$
> \begin{align} \\
>\text{Ent}(f^2(X)) &\le 2 \mathbb{E}\left[ \lVert \nabla f(X) \rVert_{2}^2 \right]  
> \end{align}
>$$ 

^dddf82

- [[Entropy Functional]]

>[!info]
>$$
>\mathcal{E}(f) := \frac{1}{2}\mathbb{E}\left[ \sum_{i=1}^{n} \left(f(X) - f(\widetilde{X}^{(i)}) \right)^2 \right] = \mathbb{E}\left[ \lVert \nabla f(X) \rVert_{2}^2 \right] 
>$$
>where 
>$$
>\lvert  \nabla f(X)  \rvert = \left\lvert  \frac{f(X) - f(\widetilde{X}^{(i)}) }{X_{i} - X_{i}^{'}}  \right\rvert= 2 \lvert f(X) - f(\widetilde{X}^{(i)})  \rvert 
>$$
>since $X_i, X_{i}^{'} \in \{ -1, 1 \}$, thus their difference is either $0$ or $2$.



>[!important] Corollary (Logarithmic Sobolev Inequality for Bernoulli Random Variables)
>If $f: \set{-1, +1}^n \to \mathbb{R}$ be an arbitrary real-valued function and $$X = (X_1 \,{,}\ldots{,}\, X_n) \in \set{-1, +1}^n$$ is a vector of **Bernoulli random variables** with $p= \mathcal{P}\set{Z_i = +1}$. 
>
>Then
>$$
> \begin{align}
> \text{Ent}(f^2) &\le c(p)\mathcal{E}(f)    
> \end{align}
>$$  
>where
>$$ 
> \begin{align*}
> c(p) &= \frac{1}{1 - 2p}\log\frac{1-p}{p}
> \end{align*}
>$$  
>Note that $\lim\limits_{p \to 1/2}c(p) = 2$.



## Explanation

















-----------
##  Recommended Notes and References

- [[Entropy Functional]]
- [[Sobolev Space]]

- [[Concentration Inequalities by Boucheron]]