---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - contravariant_tensor
topics:
  - differential_geometry
  - linear_algebra
name: Contravariant Tensor on Vector Space
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Contravariant Tensor on Vector Space

>[!important] Definition
>For any finite-dimensional real vector space $V$, we define **the space** of **contravariant tensors on $V$** of **rank** $k$ to be the vector space
>$$
> \begin{align*}
> T^{k}V &= \underbrace{V\otimes \ldots \otimes V}_{k}
> \end{align*}
>$$  

- [[Covariant Tensor on Vector Space]]

>[!important] Definition
>In particular, $T^1(V) = V$, and by convention $T^0(V) = \mathbb{R}$. 
>
>Because we are assuming that $V$ is finite-dimensional, it is possible to identify this space with **the set of multilinear functionals** of **$k$ covectors**:
>$$
> \begin{align*}
> T^{k}V &= \set{\text{multilinear functionals }\alpha: \underbrace{V^{*}\times \ldots \times V^{*}}_{k} \rightarrow \mathbb{R} }
> \end{align*}
>$$ 



## Explanation





-----------
##  Recommended Notes and References

- [[Multilinear Function]]


- [[Introduction to Smooth Manifolds by Lee]]