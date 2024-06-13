---
tags:
  - concept
  - math/linear_algebra
keywords:
  - subspace_reduce_linear_map
topics:
  - linear_algebra
name: Reducibility of Linear Transformation
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Reducibility of Linear Transformation


>[!important] Definition
>If $S$ and $W$ are both linear subspaces of vector space $V$, and *both* $S$ and $W$ are *invariant* under a linear map $A$ on $V$, and such that $V$ is the *direct sum of them*, 
>$$
>V = S \oplus W,
>$$
>then $A$ is **reduced** or **decomposed** by the pair $(S,W)$

- [[Invariance under Linear Transformation]]
- [[Direct Sum of Subspaces]]
- [[Linear Subspace]]


## Explanation



## Matrix Representation

>[!important] Definition
>Let $V$ be an $n$-dimensional vector space  with basis $(e_{1} \,{,}\ldots{,}\, e_{n})$ where  $(e_{1} \,{,}\ldots{,}\, e_{m})$ is the basis of the $m$-dimensional subspace $S$ and  $(e_{m+1} \,{,}\ldots{,}\, e_{n})$ is the basis of the $(n-m)$-dimensional complementary subspace $W$
>
>If both $S$ and $W$ is *invariant under* $A$, then the **matrix representation** of $A$ is *similar* to the form
>$$
>\boldsymbol{A} = \left[\begin{array}{cc}
>\boldsymbol{A}_{S} &  \boldsymbol{0}\\ 
> \boldsymbol{0} & \boldsymbol{A}_{W}
\end{array}\right]
>$$
>
>In this way,  $\boldsymbol{A}_{S}$ is the matrix representation of $A|_{S}$ and  $\boldsymbol{A}_{W}$ is the matrix representation of $A|_{W}$. That is,
>$$
>\begin{align*}
>A e_{j} &= \sum_{i=1}^{m}a_{i,j} e_{i}, \quad j=1 \,{,}\ldots{,}\,m\\
>A e_{j} &= \sum_{i=m+1}^{n}a_{i,j} e_{i}, \quad j=m+1 \,{,}\ldots{,}\,n\\
\end{align*}
>$$

- [[Matrix]]
- [[Invariance under Linear Transformation]]



-----------
##  Recommended Notes and References

- [[Invariance under Linear Transformation]]
- [[Linear Map]]

- [[Direct Sum of Subspaces]]
- [[Linear Subspace]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]