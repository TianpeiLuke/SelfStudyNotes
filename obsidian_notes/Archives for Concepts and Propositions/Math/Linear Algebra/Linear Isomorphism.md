---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - isomorphism
topics:
  - linear_algebra
  - functional_analysis
name: Isomorphism
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Linear Isomorphism

>[!important] Definition
>For vector space, an **(linear) isomorphism** is a *bijective linear mapping* from one *vector spaces* to another *vector space* that *preserve* the *structure* of that *vector space.* 
>That is, for vector spaces $V$ and $W$ over field $F$,  $\varphi: V \to W$ is a **linear isomorphism** if
>- $\varphi$ is a *linear map*, i.e. it preserve *the linearity of operations*
>$$
>\begin{align*}
>\varphi(x + y) &= \varphi(x) + \varphi(y), \quad \forall x, y \in V\\
>\varphi(\lambda x) &= \lambda \varphi(x), \quad \forall \lambda \in F, x\in V 
\end{align*}
>$$
>- $\varphi$ is *bijective map*, i.e. $\varphi^{-1}: W\to V$ exists and it is also a *linear map*

- [[Linear Map]]
- [[Vector Space over a Field]]


## Explanation

>[!info]
>Depending on definition of specific structure, we can have various different definition of *isomorphisms*:
> 
> - For **metric space**, an **isomorphism** is a *bijective linear operator* that *preserves* the **metric**. It is often called an **isometry**.
> - For **inner product space**, an *isomorphism* is a *surjective linear operator* that *preserves the inner product*. It is often called an **surjective isometry**.
> - For **linear algebra**, an *isomorphism* is a *bijective linear mapping* that *preserves all algebraic operations* (i.e. *the vector addition* and *scalar multiplication*).



- [[Bijective Function and Inverse Function]]



-----------
##  Recommended Notes and References

- [[Bijective Function and Inverse Function]]
- [[Homeomorphism]]
- [[Diffeomorphism]]
- [[Isometry and Isometric isomorphism]]

- [[Finite Dimensional Vector Spaces by Halmos]]