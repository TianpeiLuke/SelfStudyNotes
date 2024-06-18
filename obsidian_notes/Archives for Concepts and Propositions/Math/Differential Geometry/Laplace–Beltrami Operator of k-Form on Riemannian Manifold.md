---
tags:
  - concept
  - math/information_theory
  - math/differential_geometry
keywords:
  - laplace_beltrami_operator
  - differential_k_form
topics:
  - information_theory
  - differential_geometry
name: Laplace–Beltrami Operator of k-Form on Riemannian Manifold
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Laplace–Beltrami Operator of k-Form on Riemannian Manifold

>[!important] Definition
>Let $(M, g)$ be an *oriented* *compact Riemannian* $n$-manifold. 
>
>For each $0 \le k \le n$, the **Laplace–Beltrami operator** $$\Delta: \Omega^{k}(M) \to \Omega^{k}(M)$$  is the *linear map* defined by
>$$
>\begin{align*}
> \Delta \omega &= d\left( d^{*}\,\omega \right) + d^{*}\left( d\,\omega \right)
>\end{align*}
>$$
>where $d^{*}: \Omega^{k}(M) \rightarrow \Omega^{k-1}(M)$ is the *dual adjoint of exterior derivative* $$\left\langle d^{*} \omega, \eta  \right\rangle = \left\langle \omega , d\eta \right\rangle$$ where $\omega \in \Omega^{k}(M)$ and $\eta \in \Omega^{k-1}(M).$

- [[Adjoint of Exterior Derivative on Riemannian Manifold]]
- [[Exterior Derivatives of Differential Form]]
- [[Differential k-Form on Manifold]]
- [[Space of all Smooth k-Forms on a Manifold]]
- [[Introduction to Smooth Manifolds by Lee]] pp 464


## Explanation

>[!important]
>When $k=0$, $\Omega^{0}(M) = \mathcal{C}^{\infty}(M)$, the **Laplace–Beltrami operator** becomes the **Geometric Laplacian** $$\Delta: \mathcal{C}^{\infty}(M) \to \mathcal{C}^{\infty}(M)$$
>where
>$$
>\begin{align*}
> \Delta f &= -\text{div}(\text{grad }f)
>\end{align*}
>$$

- [[Laplacian of Smooth Map on Riemannian Manifold]]

## Properties





-----------
##  Recommended Notes and References


- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]

- [[Concepts and Theorems for Riemannian Manifold]]
- Wikipedia [Laplace_operator](https://en.wikipedia.org/wiki/Laplace_operator)