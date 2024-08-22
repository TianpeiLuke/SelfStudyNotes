---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords:
  - symmetrization_operation
topics:
  - differential_geometry
  - linear_algebra
name: Symmetrization Operation on Tensor
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Symmetrization Operation on Tensor

>[!important] Definition
>Let $S_{K}$ be a group of permutation of the set $\left\{ 1 \,{,}\ldots{,}\, k\right\}$. 
>
>Given a $k$-tensor $\alpha$ and a permutation $\sigma \in S_{k}$, we define a new $k$-tensor $^{\sigma}\alpha$ as
>$$
>^{\sigma}\alpha(v_{1} \,{,}\ldots{,}\, v_{k}) = \alpha \left( v_{\sigma(1)} \,{,}\ldots{,}\, v_{\sigma(k)} \right)
>$$

>[!info]
>Note that for any two permutations $\sigma$ and $\tau \in S_{k}$,
>$$
>^{\tau}(^{\sigma}\alpha) = ^{\tau\sigma}\alpha.
>$$

>[!important] Definition
>We define a *projection* $$\text{Sym }: T^k(V^{*}) \rightarrow \Sigma^k(V^{*}),$$ called **symmetrization**, as follows:
>$$
> \begin{align*}
> \text{Sym }\alpha &=\frac{1}{k!} \sum_{\sigma \in S_k}(^{\sigma}\alpha)
> \end{align*}
>$$  
>where $S_k$ is the **symmetric group** *on $k$ elements*. 
>
>More explicitly, this means
>$$
> \begin{align*}
> \text{Sym }\alpha(v_1, \ldots, v_k) &= \frac{1}{k!} \sum_{\sigma \in S_k} \alpha(v_{\sigma(1)}, \ldots, v_{\sigma(k)}).
> \end{align*}
>$$ 

- [[Projection Map onto Linear Subspace]]
## Explanation



## Properties

>[!important] Proposition
> Let $\alpha$ be a covariant tensor on a finite-dimensional vector space.
>  
>  - $\text{Sym }\alpha$ is **symmetric**.
>  - $\text{Sym }\alpha = \alpha$ *if and only if* $\alpha$ is symmetric.

- [[Symmetric Tensor]]



-----------
##  Recommended Notes and References

- [[Exterior Forms]]


- [[Introduction to Smooth Manifolds by Lee]]