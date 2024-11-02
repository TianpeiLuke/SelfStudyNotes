---
tags:
  - concept
  - math/differential_equation
  - math/functional_analysis
keywords:
  - linear_partial_differential_equations
  - laplace_equation
  - poisson_equation
topics:
  - differential_equation
name: Laplace Equation and Poisson Equation
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Laplace Equation and Poisson Equation


>[!important] Definition
>The **Laplace equation** is defined as follows
>$$
>\begin{align*}
> \Delta u & = 0
>\end{align*}
>$$
>where  $x\in U$, $U$ is an open set,   $u: \overline{U}  \to\mathbb{R}$, and 
>$$
>\Delta := \sum_{i}^{n}\frac{ \partial^2 }{ (\partial x^i)^2} 
>$$
>is the **Laplace differential operator** or *Laplacian operator*.

^82f52a

- [[Partial Differential Equations]]
- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Coordinate Representation of Laplace Operator]]

>[!important] Definition
>The **(linear) Poisson equation** is defined as follows
>$$
>\begin{align*}
> \Delta u & = f
>\end{align*}
>$$
>where  $x\in U$, $U$ is an open set,   $u: \overline{U}  \to\mathbb{R}$ is unknown, $f: U\to \mathbb{R}$ is given and
>$$
>\Delta := \sum_{i=1}^{n}\frac{ \partial^2 }{ (\partial x^i)^2 } 
>$$
>is the *Laplace differential operator* or *Laplacian operator*.


## Explanation

>[!important]
>The **Laplace equation** 
>$$
>\begin{align*}
> \sum_{i=1}^{n}\frac{\partial^2}{(\partial x^i)^2} u= 0.
>\end{align*}
>$$
>is **elliptic equation**. 

- [[Second-Order Elliptic Equation]]
- [[Second-Order Linear Partial Differential Equations]]

## Physical Interpretation



## Operator Equation

>[!important]
>The *Laplace equation* corresponds to the **divergence equation**
>$$
>\text{div}(V) = 0
>$$
>in $U$, where $V$ is the **gradient vector field** of *potential function*  $u$, i.e. $$V = \text{grad}(u)$$

- [[Gradient of Smooth Map]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Divergence Theorem on Riemannian Manifold]]

## Harmonic Function

- [[Harmonic Function]]


## Fourier Transform and Laplace Transform

- [[Fourier Series and Fourier Transform]]
- [[Laplace Transform]]




-----------
##  Recommended Notes and References


- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Partial Differential Equations]]

- [[Infinitesimal Generator of Brownian Motion and Laplacian]]

- [[Fourier Series and Fourier Transform]]


- [[Partial Differential Equations by Evans]]