---
tags:
  - concept
  - math/abstract_algebra
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - polynomial_ring
topics:
  - abstract_algebra
name: Polynomial Ring
date of note: 2024-10-11
---

## Concept Definition

>[!important]
>**Name**: Polynomial Ring

>[!important] Definition
>Let $(R, +, \cdot)$ be a *ring*. 
>
>The formal sum  $$p_{n}(x) = a_{n}x^{n} + a_{n-1}x^{n-1}\,{+}\ldots{+}\,a_{1}x + a_{0}$$ is called a **polynomial** in $x$ with *coefficients* $a_{i}\in R.$
>where
>- $x$ is an **indeterminate**.
>- $n\in \mathbb{N}$, and $a_{i}\in R,\, i=0\,{,}\ldots{,}\,n$ are **coefficients**
>- If  $a_{n} \neq 0$,  $p_{n}(x)$ is referred to as a **polynomial of degree $n$**.
>	- $a_{n}x^{n}$ is called the **leading term** and $a_{n}$ is the **leading coefficient**.
>- A polynomial is called **monic** if $a_{n} = 1$, i.e. $$p_{n}(x) = x^{n} + a_{n-1}x^{n-1}\,{+}\ldots{+}\,a_{1}x + a_{0}$$

- [[Ring]]
- [[Ring with Identity]]

>[!important] Definition
>The set of polynomials $p_{n}(x)$ for all $n \in \mathbb{N}$ is called the **ring of polynomials** in variable $x$ with *coefficients* in $R$, denoted as
>$$
>R[x] := \left\{  a_{n}x^{n} \,{+}\ldots{+}\,a_{1}x + a_{0}\;|\; n\in \mathbb{N}, a_{i}\in R,\, i=0\,{,}\ldots{,}\,n \right\} 
>$$
 

## Explanation





-----------
##  Recommended Notes and References




- [[Characteristic Polynomial for Linear Map]]
- [[Continuous Functional Calculus]]
- [[Companion Matrix of Polynomial]]
- [[Krylov Subspace Methods]]


- [[Abstract Algebra by Dummit]] pp 234, 295