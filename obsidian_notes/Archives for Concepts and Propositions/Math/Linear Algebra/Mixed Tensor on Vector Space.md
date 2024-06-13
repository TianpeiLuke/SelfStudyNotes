---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - mixed_tensor
topics:
  - differential_geometry
  - linear_algebra
name: Mixed Tensor on Vector Space
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Mixed Tensor on Vector Space

>[!important] Definition
>For any finite-dimensional real vector space $V$, we define **the space** of **mixed tensors on $V$** of **type** $(k, l)$ to be the vector space
>$$
> \begin{align*}
> T^{(k,l)}V &= \underbrace{V\otimes \ldots \otimes V}_{k} \otimes \underbrace{V^{*}\otimes \ldots \otimes V^{*}}_{l}
> \end{align*}
>$$  

- [[Covariant Tensor on Vector Space]]
- [[Contravariant Tensor on Vector Space]]

## Explanation

>[!example] 
>Some of these spaces are identical:
>$$
> \begin{align*}
> T^{(0,0)}V &= T^0V = T^{0}V^{*} =  \mathbb{R}\\
> T^{(0,1)}V &= T^{1}V^{*} = V^{*}\\
> T^{(1,0)}V &= T^{1}V = V\\
> T^{(k,0)}V &= T^{k}V \\
> T^{(0,k)}V &= T^{k}V^{*}
> \end{align*}
>$$ 

- [[Covariant Tensor on Vector Space]]
- [[Contravariant Tensor on Vector Space]]



-----------
##  Recommended Notes and References

- [[Abstract Tensor Product]]
- [[Multilinear Function]]


- [[Introduction to Smooth Manifolds by Lee]]