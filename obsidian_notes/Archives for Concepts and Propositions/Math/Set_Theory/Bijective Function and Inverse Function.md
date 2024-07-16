---
tags:
  - concept
  - math/set_theory
keywords:
  - bijective_function
  - inverse_function
topics:
  - set_theory
name: bijective function; inverse_function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Bijective Function and Inverse Function

>[!important] Definition
>A function $f: X\to Y$ is **bijective** or is an **one-to-one correspondence** if it is both **injective** and **surjective**

- [[Injective Function]]
- [[Surjective Function]]

>[!important] Definition
>A function is **bijective** if and only if it is **invertible**; that is, 
>
>A function $f:X \to Y$ is bijective *if and only if* there is a function $g: Y \to X$, called the **inverse** of f, such that each of the two ways for *composing* the two functions produces an identity function: for every $x\in X$ and $y\in Y$,
>$$
>\begin{align*}
>(f \circ g)(y) &= y\\
>(g \circ f)(x) &= x
\end{align*}
>$$


## Explanation

>[!info]
>A bijection is a **relation** between two sets such that each element of either set is **paired with exactly one element** of the other set.

>[!important]
>Bijective function defines an **equivalent** relationship between domain and co-domain.

>[!example]
>A class of important bijections are **isomorphism**, which identifies *two sets* with **the same structure**. Thus these two sets are seen as equivalent under the perspective of the corrresponding field
>- **General Structure**: isomorphism
>- **Linear Algebraic Structure**: linear isomorphism [[Linear Isomorphism]]
>- **Group Algebraic Structure**: group isomorphism [[Isomorphism between Groups]]
>- **Ring Algebraic Structure**: ring isomorphism
>- **Graph Structure**: graph isomorphism [[Graph Isomorphism]]
>- **Topological Structure**: homeomorphism [[Homeomorphism]]
>- **Differential Structure**: diffeomorphism: [[Diffeomorphism]]
>- **Metric Structure**:  isometry [[Isometry and Isometric isomorphism]]
>- **Metric and Linear Structure**: isometric isomorphism [[Isometry and Isometric isomorphism]]



>[!important]
>If $f: X\to Y$ is **bijective**, then the domain has the same number of element as the co-domain 
>$$
>\lvert X \rvert = \lvert Y \rvert.  
>$$




-----------
##  Recommended Notes and References

- [[Function]]
- [[Topology Book by Munkres]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
