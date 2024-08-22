---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords:
  - alternation_operation
topics:
  - differential_geometry
  - linear_algebra
name: Alternation Operation on Tensor
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Alternation Operation on Tensor

>[!info] Definition
>Let $S_{K}$ be a group of permutation of the set $\left\{ 1 \,{,}\ldots{,}\, k\right\}$. 
>
>Given a $k$-tensor $\alpha$ and a permutation $\sigma \in S_{k}$, we define a new $k$-tensor $^{\sigma}\alpha$ as
>$$
>^{\sigma}\alpha(v_{1} \,{,}\ldots{,}\, v_{k}) = \alpha \left( v_{\sigma(1)} \,{,}\ldots{,}\, v_{\sigma(k)} \right)
>$$

>[!important] Definition
>We define a *projection* $$\text{Alt }: T^k(V^{*}) \rightarrow \Lambda^k(V^{*}),$$ called **alternation**, as follows:
>$$
> \begin{align*}
> \text{Alt }\alpha &=\frac{1}{k!} \sum_{\sigma \in S_k}(\text{sgn}(\sigma))(^{\sigma}\alpha)
> \end{align*}
>$$  
>where $S_k$ is the **symmetric group** *on $k$ elements*. 
>
>More explicitly, this means
>$$
> \begin{align*}
> \text{Alt }\alpha(v_1, \ldots, v_k) &= \frac{1}{k!} \sum_{\sigma \in S_k} (\text{sgn}(\sigma)) \alpha(v_{\sigma(1)}, \ldots, v_{\sigma(k)}).
> \end{align*}
>$$ 

- [[Determinant of Linear Transformation]]
- [[Projection Map onto Linear Subspace]]

## Explanation





-----------
##  Recommended Notes and References

- [[Exterior Forms]]


- [[Introduction to Smooth Manifolds by Lee]]