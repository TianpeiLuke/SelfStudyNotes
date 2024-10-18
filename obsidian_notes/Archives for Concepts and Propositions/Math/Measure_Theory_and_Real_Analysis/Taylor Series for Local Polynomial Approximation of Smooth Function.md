---
tags:
  - concept
  - math/real_analysis
keywords:
  - taylor_expansion
  - taylor_series
topics:
  - real_analysis
name: Taylor Series for Local Polynomial Approximation of Smooth Function
date of note: 2024-10-17
---

## Concept Definition

>[!important]
>**Name**: Taylor Series for Local Polynomial Approximation of Smooth Function

### 1-Dimensonal Case

>[!important] Taylor's Theorem
>Suppose 
>- $f: [a,b] \to \mathbb{R}$ is a *real function* on $[a,b]$, 
>- $n$ is a positive integer, 
>- the *$(n-1)$-th derivatives* $f^{(n-1)}$ is **continuous** on $[a,b]$, 
>- the $n$-th derivative $f^{(n)}$ **exists** for every $t\in (a,b)$.
>  
>Let $\alpha, \beta$ be distinct points of $[a,b]$, and define *the polynomial*
>$$
>P_{n-1}(x) := \sum_{k=0}^{n-1} \frac{f^{(k)}(\alpha)}{k!} \;(x - \alpha)^{k}.
>$$
>
>Then there **exists** a point $\theta \in (\alpha, \beta)$ such that $$f(\beta) = P_{n-1}(\beta) + \frac{f^{(n)}(\theta)}{n!}\,(\beta - \alpha)^{n}$$  

- [[Polynomial Ring]]
- [[Continuous Function]]
- [[Smooth Map]]

>[!important] Definition
>Suppose 
>- $f: [a,b] \to \mathbb{R}$ is a *real function* on $[a,b]$, 
>- $n$ is a positive integer, 
>- the *$(n-1)$-th derivatives* $f^{(n-1)}$ is **continuous** on $[a,b]$, 
>- the $n$-th derivative $f^{(n)}$ **exists** for every $t\in (a,b)$.
>  
>Then the following polynomial is called the **Taylor expansion** of $f$ at $x_{0}$
>$$
>f(x) = f(x_{0}) + f^{(1)}(x_{0})\;(x - x_{0}) + \frac{1}{2}(f^{(2)}(x_{0}))^2(x - x_{0})^2 \,{+}\ldots{+}\,\frac{f^{(n-1)}(x_{0})}{(n-1)!} \;(x - x_{0})^{n-1} +\frac{f^{(n)}(\theta)}{n!}\,(x - x_{0})^{n}
>$$  
>where
>- $x \in B(x_{0}, d)$ is in the *small neighborhood* of $x_{0}$
>- and $\theta \in (x_{0}, x)$ is a fixed point.



## Explanation


### Compare to Fourier Series

- [[Fourier Series and Fourier Transform]]



-----------
##  Recommended Notes and References




- [[Principles of Mathematical Analysis by Rudin]] pp 110, 116, 176