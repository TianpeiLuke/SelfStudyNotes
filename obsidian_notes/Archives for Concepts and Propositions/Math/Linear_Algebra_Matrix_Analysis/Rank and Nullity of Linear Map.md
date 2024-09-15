---
tags:
  - concept
  - math/linear_algebra
keywords:
  - rank_linear_map
  - nullity_linear_map
topics:
  - linear_algebra
name: Rank and Nullity of Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Rank and Nullity of Linear Map

>[!important] Definition
>Let $V$ and $W$ be finite dimensional vector spaces and $A: V \to W$ be a linear transformation.
>
>The **rank of $A$** is defined as the *dimension* of the *range* of $A$
>$$
>\text{rank}(A) := r(A) := \text{dim}\left( \text{Im}(A) \right) = \text{dim}\left\{ Av: v\in V \right\} 
>$$

- [[Range and Kernel of Linear Map]]

>[!important] Definition
>The **nullity** of linear map $A: V \to W$ is defined as the *dimension* of its *kernel (null-space)*
>$$
>\text{nullity}(A) = \nu(A) := \text{dim}(\text{Ker}(A)) = \text{dim}\left\{ v\in V: Av = 0 \right\}. 
>$$

- [[Range and Kernel of Linear Map]]


## Explanation

>[!important]
>Under given coordinate system, the **rank of linear map** $A$ is equal to **the row rank** and **column rank** of the **matrix** $\boldsymbol{A}$.

## Property




## Rank and Nullity Formula

>[!important] Proposition
>If $A$  is a linear transformation on *$n$-dimensional* vector space $V$, and if $S$ is *any $m$-dimensional subspace* of $V$, then **the dimension of image of $S$ under $A$** is
>$$
>\text{dim}(AS) \ge m - \text{nullity}(A)
>$$


>[!important] Proposition
>If $A$ and $B$ are both linear transformation on a finite-dimensional vector space $V$, then the **rank of sum of map** is *bounded above* by the **sum** of **each map's rank**
>$$
>\text{rank}(A + B) \le \text{rank}(A) + \text{rank}(B)
>$$


>[!important] Proposition (Sylvester's Law of Nullity)
>If $A$ and $B$ are both linear transformation on a finite-dimensional vector space $V$, then
>- the **rank of product map** is *bounded above* by the **minimal** of **each map's rank**
>$$
>\text{rank}(A\,B) \le \min \left\{ \; \text{rank}(A) \;,\; \text{rank}(B) \;\right\}
>$$
>- the **nullity of product map** is *bounded above* by the **sum** of **each map's nullity**
>$$
>\text{nullity}(A\,B) \; \le \;  \text{nullity}(A) +\text{nullity}(B) 
>$$



>[!important] Proposition
>If $A$ and $B$ are both linear transformation on a finite-dimensional vector space $V$, and if $B$ is **invertible**,  then the **rank of product map** is 
>$$
>\text{rank}(AB) = \text{rank}(BA) = \text{rank}(A)
>$$
>That is, the **rank is invariant** under *__invertible__ linear transformation*.

### Rank-Nullity Theorem

- [[Rank–Nullity Theorem]]



-----------
##  Recommended Notes and References

- [[Range and Kernel of Linear Map]]

- [[Linear Map]]
- [[Vector Space over a Field]]

- [[Kernel of Group Homomorphism]]
- [[Image of Group Homomorphism]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]] pp 90