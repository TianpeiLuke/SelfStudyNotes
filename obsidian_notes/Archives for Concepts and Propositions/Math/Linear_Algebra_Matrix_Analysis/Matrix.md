---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
  - math/matrix_analysis
keywords:
  - matrix
topics:
  - linear_algebra
  - functional_analysis
name: Matrix
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Matrix

>[!important] Definition
>Let $V$ be a $n$-dimensional vector spaces over the same field $F$, and let $E = (\epsilon_{1} \,{,}\ldots{,}\,\epsilon_{n})$ be any *basis* in $V$.
>
>Denote $A: V \to V$ as a *linear transformation* on $V$. Since any vector can be represented as a linear combination of basis, we have
>$$
>A\epsilon_{i} = \sum_{j=1}^{n}a_{i,j}\epsilon_{j}, \quad i=1 \,{,}\ldots{,}\,n. 
>$$
>
>Thus the linear functional $A$ can be *represented* by $n \times n$ scalars $[a_{i,j}]$. By arranging the subscript $i$ and $j$ as rows and columns, we have the form
>$$
> \begin{align*}
> \boldsymbol{A} := \left[\begin{array}{cccc}
>a_{1,1} & a_{1,2} & \dots & a_{1,n} \\
> a_{2,1} & a_{2,2} & \dots & a_{2,n} \\ 
> \dots & \dots & \dots & \dots\\
> a_{n,1} & a_{n,2} & \dots & a_{n,n} \\
> \end{array}\right]
> \end{align*}
> $$ 
>This representation of *linear transformation* $A$ *under a basis* $E$ is called a **matrix.** 

- [[Linear Map]]
- [[Basis of Vector Space]]
- [[Vector Space over a Field]]



## Explanation

>[!important]
>It is critical to understand that the matrix $\boldsymbol{A}$ is a representation of linear transformation **under a given basis** $E$.
>
>**Change a basis / coordinate system** will lead to *change of the matrix representation*. 

>[!info]
>Matrix representation is only available under **finite dimensional** vector space.



-----------
##  Recommended Notes and References


- [[Bounded Linear Functional]]
- [[Vector Space over a Field]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]