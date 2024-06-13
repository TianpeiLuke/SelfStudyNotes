---
tags:
  - concept
  - math/linear_algebra
keywords:
  - invariance_linear
topics:
  - linear_algebra
name: Invariance under Linear Transformation
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Invariance under Linear Transformation

>[!info]
>A possible **relation** between *subspaces* $S$ of a vector space and *linear transformations* $A$ on that space is **invariance**.

>[!important] Definition
>We say that  a linear subspace $S$ of $V$ is **invariant under linear transformation** $A$ if 
>$$
>x \in M \implies Ax \in M
>$$


## Explanation

>[!info]
>We know that a *subspace* of a vector space is itself a vector space; if we know that $S$ is **invariant under $A$**, we may *ignore* the fact that $A$ is defined *outside* $S$ and we may *consider $A$ as a linear transformation defined on the vector space $S$*. 
>
>**Invariance** is often considered for **sets of linear transformations**, as well as for a *single one*; $S$ is **invariant under a set** if it is *invariant under each member* of the set.

>[!info]
>For subspace $S$ of $V$, there are many ways to define its complementary $W$ so that $V = S \oplus W$. 
>
>Even if $S$ is invariant under $A$, it may be possible that none of its complementary $W$ are invariant under $A$ as well. 
>
>If there exists one $W$, we say that $A$ is **reduced** by the pair $(S, W).$ 

- [[Reducibility of Linear Transformation]]

## Matrix Representation

>[!important] Definition
>Let $V$ be an $n$-dimensional vector space  with basis $(e_{1} \,{,}\ldots{,}\, e_{n})$ and $S$ be the $m$-dimensional subspace  with basis   $(e_{1} \,{,}\ldots{,}\, e_{m})$ with $m < n$.
>
>If $S$ is *invariant under* $A$, then the **matrix representation** of $A$ is *similar* to the form
>$$
>\boldsymbol{A} = \left[\begin{array}{cc}
>\boldsymbol{A}_{S} &  \boldsymbol{0}\\ 
> \boldsymbol{A}_{S, S^{\bot}} & \boldsymbol{A}_{S^{\bot}}
\end{array}\right]
>$$
>
>In this way,  $\boldsymbol{A}_{S}$ is the matrix representation of $A|_{S}$ as considered as *a linear transformation on $S$*.
>$$
>\begin{align*}
>A e_{i} &= \sum_{j=1}^{m}a_{i,j} e_{j}, \quad i=1 \,{,}\ldots{,}\,m\\
>A e_{i} &= \sum_{j=1}^{m}a_{i,j} e_{j} + \sum_{j=m+1}^{n}a_{i,j} e_{j}, \quad i=m+1 \,{,}\ldots{,}\,n\\
\end{align*}
>$$

- [[Matrix]]




-----------
##  Recommended Notes and References

- [[Matrix]]
- [[Linear Map]]

- [[Linear Subspace]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]