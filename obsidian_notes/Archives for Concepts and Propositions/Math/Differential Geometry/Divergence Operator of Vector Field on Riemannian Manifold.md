---
tags:
  - concept
  - math/differential_geometry
keywords:
  - divergence_operator
topics:
  - differential_geometry
name: Divergence of Vector Field on Riemannian Manifold
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Divergence of Vector Field on Riemannian Manifold

>[!important] Definition
>Let $(M, g)$ be an *oriented Riemannian $n$-manifold* (with or without boundary). 
>
>We define the multiplication by the *Riemannian volume form* as a **smooth bundle isomorphism**: $*: \mathcal{C}^{\infty}(M) \to \Omega^{n}(M)$:
>$$
>*f := f\; dV_{g}
>$$
>where *the Riemannian volume* form is defined as
>$$
>dV_{g} := \sqrt{ \det(g_{i,j}) }\;\; dx^1 \ldots dx^n
>$$

- [[Hodge Star Operator on Riemannian Manifold]]
- [[Riemannian Volume Form]]
- [[Orientation of Manifolds]]

>[!important] Definition
>Define a **smooth bundle isomorphism** $\beta: \mathfrak{X}(M) \to \Omega^{n-1}(M)$ as follows:
>$$
>\beta(X) = X \mathbin{\lrcorner }\,dV_{g}
>$$
>That is, it is *the interior product* of the *Riemannian volume form* by $X$.

- [[Interior Multiplication]]

>[!important] Defintion
>Let $(M, g)$ be an *oriented Riemannian $n$-manifold* (with or without boundary). 
>
>Define the **divergence operator** $\text{div}: \mathfrak{X}(M) \to \mathcal{C}^{\infty}(M)$ by
>$$
>\text{div }X := *^{-1}\;d\left( \beta(X) \right)
>$$
>or, equivalently, 
>$$
>d\left( X \mathbin{\lrcorner }\,dV_{g} \right) = \left( \text{div }X \right)\,dV_{g}
>$$

- [[Exterior Derivatives of Differential Form]]

## Explanation

>[!important]
>The *divergence operator* maps a **vector field** into a **smooth function**.


## Coordinate Representation

- [[Coordinate Representation of Divergence Operator]]


## Properties

>[!important] Proposition
>Let $(M, g)$ be a **compact Riemannian manifold** with boundary. Let $\widetilde{g}$ denote the *induced Riemannian metric* on $\partial M$, and let $N$ be the **outward** unit **normal vector field** along $\partial M$.
>
>Then 
>- the **divergence operator**  $\text{div}: \mathfrak{X}(M) \to \mathcal{C}^{\infty}(M)$   satisfies the following **product rule**: 
>  $$
> \begin{align*}
> \text{div}\left( f\,X \right) &= f\,\text{div}(X) + \left\langle \text{grad }f ,  X\right\rangle_{g}.
> \end{align*}
> $$
>- And the following **integration by parts** holds
>  $$
> \begin{align*}
>  \int_{M}\left\langle \text{grad }f ,  X\right\rangle_{g}\,dV_{g} &= - \int_{M}\left( f\,\text{div}(X)  \right)\,dV_{g} + \int_{\partial M} f\left\langle X , N \right\rangle dV_{\widetilde{g}}.
> \end{align*}
> $$


- [[Integration by Parts]]
- [[Introduction to Smooth Manifolds by Lee]] pp 436

## Divergence Theorem

- [[Divergence Theorem on Riemannian Manifold]]


## Geometric Interpretation of Divergence


>[!info]
>The term *“divergence”* is used because of the following geometric interpretation. 

>[!important] Definition
>A smooth flow $\theta$ on $M$ is said to be **volume-preserving** if for every *compact regular domain* $D$, we have 
>$$
>\text{Vol}\left( \theta_{t}(D) \right) = \text{Vol}\left( D \right)
>$$
>whenever the *domain* of $\theta_{t}$ contains $D$.

>[!important] Definition
>Similarly,
>- $\theta_{t}$ is  **volume-increasing** if $\text{Vol}\left( \theta_{t}(D) \right) > \text{Vol}\left( D \right)$;
>- $\theta_{t}$ is  **volume-decreasing** if $\text{Vol}\left( \theta_{t}(D) \right) < \text{Vol}\left( D \right)$;
>- $\theta_{t}$ is  **volume-nondecreasing** if $\text{Vol}\left( \theta_{t}(D) \right) \ge \text{Vol}\left( D \right)$;
>- $\theta_{t}$ is  **volume-nonincreasing** if $\text{Vol}\left( \theta_{t}(D) \right) \leq \text{Vol}\left( D \right)$;
>  
>respectively, as a function of $t$.

>[!important] Proposition (Geometric Interpretation of the Divergence)
>Let $M$ be an *oriented Riemannian manifold*, let $X \in \mathfrak{X}(M)$, and let $\theta_{t}$ be the **flow** of $X$. 
>
>Then $\theta_{t}$ is 
>- (a) **volume-preserving** *if and only if* $$\text{div}(X) = 0$$ *everywhere* on $M$.
>- (b) **volume-nondecreasing** *if and only if* $$\text{div}(X) \ge 0$$ *everywhere* on $M$.
>- (c) **volume-nonincreasing** *if and only if* $$\text{div}(X) \le 0$$ *everywhere* on $M$ . 
>- (d) **volume-increasing** *if and only if* $$\text{div}(X) > 0$$ on a *dense subset* of $M$. 
>- (e) **volume-decreasing** *if and only if* $$\text{div}(X) < 0$$ on a *dense subset* of $M$.

- [[Divergence Theorem on Riemannian Manifold]]
- [[Global Flow on Smooth Manifold]]




-----------
##  Recommended Notes and References

- [[Exterior Derivatives of Differential Form]]
- [[Interior Multiplication]]
- [[Riemannian Volume Form]]
- [[Orientation of Manifolds]]


- [[Riemannian Metric and Riemannian Manifold]]
- [[Differential k-Form on Manifold]]


- [[Laplacian of Smooth Map on Riemannian Manifold]]


- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
- Wikipedia [Divergence](https://en.wikipedia.org/wiki/Divergence)