---
tags:
  - concept
  - math/convex_analysis
keywords:
  - affine_map
topics:
  - convex_analysis
name: Affine Map
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Affine Map

>[!important] Definition
>Let $A$ and $B$ be two *affine spaces* whose associated vector spaces are $V$ and $W$.
>
>An **affine map** or **affine homomorphism** is a map $f: A \to B$ such that the map $\bar{f}: V \to W$ 
>$$
>b -a \mapsto f(b) - f(a)
>$$
>is a *well defined* *linear map*, which means
>$$
>b -a = d -c \implies f(b) - f(a) = f(d) - f(c).
>$$

- [[Linear Map]]
- [[Affine Space]]



## Explanation

>[!info]
>By definition, $f: A \to B$ is an *affine map* then there exists a *linear map* $\bar{f}: V \to W$ such that 
>$$
>f(a + v) = f(a) + \bar{f}(v)
>$$
>for all $a\in A$, and $v\in V$ associated with $A$.
>
>- The addition on the left is the additive group action associated with $(A, V, +)$;
>- The addition on the right is the additive group action associated with $(B, W, +).$ 



-----------
##  Recommended Notes and References


- [[Linear Map]]
- [[Affine Space]]

- [[Convex Analysis by Rockafellar]]
- [[Matrix Analysis by Horn]]

- Wikipedia [Affine space](https://en.wikipedia.org/wiki/Affine_space)