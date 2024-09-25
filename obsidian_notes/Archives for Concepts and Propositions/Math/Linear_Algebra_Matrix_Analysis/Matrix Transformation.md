---
tags:
  - concept
  - math/linear_algebra
keywords:
  - matrix_transformation
topics:
  - linear_algebra
name: Matrix Transformation
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Matrix Transformation

>[!important] Theorem
>Among the set of all matrices,  we define 
>- the **sum** of matrices 
>  $$
>  [a_{i,j}]_{i,j} + [b_{i,j}]_{i,j} = [a_{i,j} + b_{i,j}]_{i,j}
> $$
>- the **scalar product** of matrices 
>  $$
>  \lambda\, [a_{i,j}]_{i,j} = [\lambda\, a_{i,j}]_{i,j}
> $$
>- the **matrix product** 
> $$
>  [a_{i,j}]_{i,j} \cdot [b_{i,j}]_{i,j}  = \left[\sum_{j=1}^{n} a_{i,j}b_{j,k}\right]_{i,k}
>$$  
>- the **zero matrix**
>  $$
>  \boldsymbol{0} = [0]_{i,j}
> $$
>- the **identity matrix**
> $$
> \boldsymbol{I} = [\delta_{i,j}]_{i,j}
>$$ 
>
>Then under an arbitrary coordinate system $(e_{1} \,{,}\ldots{,}\, e_{n})$ of the $n$-dimensional vector space $V$,  the correspondence between all linear transformations $A$ on $V$ and all matrices $[a_{i,j}]_{i,j}$, described by
>$$
>Ae_{i} = \sum_{j=1}^{n}a_{i,j}e_{j}
>$$
>is an **isomorphism**; in other word, it is an **one-to-one correspondence** that preserve *sum*, *scalar product*, *matric product*, *zero* and $1$.

- [[Matrix]]
- [[Linear Isomorphism]]
- [[Linear Map]]
- [[Vector Space over a Field]]

## Explanation

>[!info]
>Let $L(V)$ be the space of linear map on $V$, where $V$ is $n$-dimensional vector space, then
>$$
>L(V) \simeq \mathbb{R}^{n \times n}
>$$


## Row and Column Operations

- [[Elementary Row and Column Operations]]



-----------
##  Recommended Notes and References

- [[Matrix]]
- [[Linear Isomorphism]]
- [[Linear Map]]

- [[Vector Space over a Field]]




- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]