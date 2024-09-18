---
tags:
  - concept
  - math/topology
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - isometry
  - isometric_isomorphism
topics:
  - topology
  - linear_algebra
  - functional_analysis
name: Isometry and Isometric isomorphism
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Isometry and Isometric Isomorphism

### Metric Space


>[!important] Definition (Metric Space)
>Let $(X, d_{X})$ and $(Y, d_{Y})$ be two metric spaces. A map $f: X \to Y$ is called an **isometry** (or **congruence** or **distance preserving map**) if for any $x, y \in X$
>$$
>\begin{align*}
> d_{X}(x, y) &= d_{Y}\left(f(x), f(y)\right)
\end{align*}
>$$
>That is, $f$ preserve *the metric* between $x, y$.
>
>$(X, d_{X})$ and $(Y, d_{Y})$ are said to be **isometric** if such $f$ exists.

- [[Metric Space]]


>[!important] Definition
>A **global isometry**, **isometric isomorphism** or **congruence mapping** is a *bijective* isometry

- [[Homeomorphism]]

>[!info]
>Other names for bijective isometry:
>- **isometric isomorphism**
>- **congruence mapping**
>- **congruence**
>- **global isometry**


### Normed Vector Space and Inner Product Space


>[!important] Definition (Normed Space)
>Let $V$ and $W$ be two *normed vector space*. 
>
>A **linear isometry** is a linear map $T: V \to W$ that *preserves the norms*
>$$
>\lVert Tv \rVert_{W} = \lVert v \rVert_{V}  
>$$
>for all $v \in V.$
>
>If $V$ and $W$ are inner product spaces, then the linear isometry also *preserves inner products*
>$$
>\left\langle Tv , Tw \right\rangle_{W} = \left\langle v , w \right\rangle_{V}
>$$

- [[Norm and Normed Space]]
- [[Inner Product Space]]

### Local Isometry on Riemannian Manifold

- [[Riemannian Metric and Riemannian Manifold]]


## Explanation


>[!info] Proposition
>An *isometry* is **injective**.

>[!info] Proposition
>An *isometry* is **continuous**.



>[!important]
>A *linear isometry* is a **global isometry**


>[!info]
>An isometry *preserves*
>- **metric and distance** for metric space
>- **length** for normed space
>- **angle** for inner product space


>[!important]
>For two inner product space $V$ and $W$, a linear isometry $T: V \to W$ **may not be unitary** as it requires $V = W$ and $T\,T^{*} = I$.
>
>On the other hand, an **unitary operator** $U: V \to V$ is a linear isometry on $V$

- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Unitary Operator in Hilbert Space]]
- [[Unitary Group]]





-----------
##  Recommended Notes and References

- [[Bijective Function and Inverse Function]]
- [[Homeomorphism]]
- [[Diffeomorphism]]

- [[epsilon Isometry]]

- [[Linear Map]]
- [[Unitary Operator in Hilbert Space]]
- [[Unitary Group]]
