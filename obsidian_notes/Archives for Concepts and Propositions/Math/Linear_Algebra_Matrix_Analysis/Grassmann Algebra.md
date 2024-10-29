---
tags:
  - concept
  - math/abstract_algebra
  - math/differential_geometry
keywords:
  - grassmann_algebra
  - exterior_algebra
topics:
  - algebra
  - differential_geometry
name: Grassmann Algebra
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Grassmann Algebra or *Exterior Algebra*

>[!important] Definition
>For any $n$-dimensional vector space $V$, define a *vector space* $\Lambda(V^{*})$ by
>$$
> \begin{align*}
> \Lambda(V^{*}) &= \bigoplus_{k=0}^{n} \Lambda^k(V^{*}).
> \end{align*}
>$$ 
> 
> It follows from Proposition [[Wedge Product]] that $$\text{dim }\Lambda(V^{*}) = 2^n.$$ 
> 
> The wedge product turns $\Lambda(V^{*})$ into an *associative algebra*, called **the exterior algebra** (or **Grassmann algebra**) of $V$.  

- [[Wedge Product]]
- [[Vector Space over a Field]]

>[!info]
>An algebra $A$ is said to be **graded** if it has a *direct sum decomposition* 
>$$A = \bigoplus_{k\in \mathbb{Z}}A^k$$ 
>such that the *product* satisfies 
>$$(A^k)(A^l) \subseteq A^{k+l}$$ 
>for each $k$ and $l$.
>
 >A graded algebra is **anticommutative** if the product satisfies $$ab = (-1)^{kl}ba$$ for $a \in A^k$, $b \in A^l$.  
 >
 >So $\Lambda(V^{*})$ is an **anticommutative graded algebra**.

- [[Graded Algebra]]

## Explanation





-----------
##  Recommended Notes and References

- [[Wedge Product]]
- [[Exterior Forms]]

- [[Vector Space over a Field]]

- [[Introduction to Smooth Manifolds by Lee]]