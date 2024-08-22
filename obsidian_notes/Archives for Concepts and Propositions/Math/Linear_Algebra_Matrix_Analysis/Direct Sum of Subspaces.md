---
tags:
  - concept
  - math/linear_algebra
keywords:
  - direct_sum
topics:
  - linear_algebra
name: Direct Sum of Subspaces
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Direct Sum of Subspaces

>[!important] Definition
>Let $U$ and $V$ be vector spaces over the same field $F$. The **direct sum** of $U$ and $V$ is a *vector space* $W$, denoted as $U \oplus V$,  whose elements are all the ordered pair $(x, y)$ with $x\in U$ and $y\in V$, with *linear operations* defined as
>$$
>\alpha_{1}(x_{1}, y_{1}) + \alpha_{2}(x_{2}, y_{2}) = (\alpha_{1}x_{1} + \alpha_{2}x_{2}, \alpha_{1}y_{1} + \alpha_{2}y_{2} )
>$$

>[!info]
>It is custom to write the ordered pair $(x, y)$ as $x+y$.
>
>The following theorem provide **alternative definitions**

>[!important] Theorem
>If $U$ and $W$ are all *subspaces* of $V$, then the following conditions are **equivalent**
>
>- $V = U \oplus W$;
>- $U \cap W = \emptyset$, and $U + W = V$, i.e. $U$ and $W$ are *complements* of each other.
>- Every vector $v \in V$ can be **uniquely** written as
>  $$
>  v = u + w, \quad u\in U, w \in W.
> $$  

- [[Linear Subspace]]


## Explanation


## Properties:


>[!important] Proposition
>Let $U$ and $W$ be *subspaces* of $V$. Then the **dimension** of the **direct sum** of $U$ and $V$ is
>$$
>\text{dim}(U \oplus W) = \text{dim}(U) + \text{dim}(W)
>$$


>[!important] Proposition
>Let $V$ be a $(n+m)$-dimensional vector space and if $U$ is any $n$-dimensional *subspace*.
>
 Then there exists an  **$m$-dimensional** subspace $W$ of $V$ such that
>$$
>U \oplus W = V
>$$

>[!info]
>In other word, every subspace in finite dimensional vector space has a **complement**.

>[!important]
>The **dimension** of the *complement* of a subspace $U \subset V$ is called **co-dimension**.
>
>For $m$-dimensional subspace in a $n$-dimensional space, the co-dimension is $n-m.$

## Dual of Direct Sum

- [[Direct Sum of Subspaces]]

-----------
##  Recommended Notes and References

- [[Direct Sum of Hilbert Spaces]]
- [[Linear Subspace]]
- [[Vector Space over a Field]]

- [[Finite Dimensional Vector Spaces by Halmos]]