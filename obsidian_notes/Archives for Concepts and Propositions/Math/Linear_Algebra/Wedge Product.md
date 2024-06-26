---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords:
  - wedge_product
topics:
  - differential_geometry
  - linear_algebra
name: Wedge Product
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Wedge Product or *Exterior Product*

>[!important] Definition
>Let $V$ be a finite-dimensional real vector space. 
>
>Given $\omega \in \Lambda^k(V^{*})$ and $\eta \in \Lambda^l(V^{*})$, we define their **wedge product** or **exterior product** to be the following *$(k+ l)$-covector*:
>$$
> \begin{align}
> \omega \wedge \eta &= \frac{(k+l)!}{k! \,l!}\text{Alt}\left(\omega \otimes \eta\right) =   \frac{1}{k! \,l!}\sum_{\sigma \in S_{k+l}} \left(\text{sgn}(\sigma)\right)\left(^{\sigma}\left(\omega \otimes \eta\right)\right)
> \end{align}
>$$ 

- [[Projection of Tensor on Alternating Tensor Space]]


## Explanation



>[!info]
>The wedge product corresponds to the determinant of matrix product
>$$
>\omega \wedge \eta = \det(|\boldsymbol{A}\boldsymbol{B}|)
>$$
>where $\omega \mapsto \det\boldsymbol{A}$ and $\eta \mapsto \det\boldsymbol{B}$ 



-----------
##  Recommended Notes and References

- [[Exterior Forms]]

- [[Introduction to Smooth Manifolds by Lee]]