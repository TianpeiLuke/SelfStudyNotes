---
tags:
  - concept
  - math/abstract_algebra
keywords:
  - group_homomorphism
topics:
  - algebra
  - abstract_algebra
name: Homomorphism between Groups
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Homomorphism between Groups

>[!important] Definition
>Given two *groups*, $(G,∗)$ and $(H,\cdot)$, a **group homomorphism** from $(G,∗)$ to $(H,\cdot)$ is a *function*  $h: G\to H$ such that for all $u, v \in G$,  it holds that
>$$
>h(u * v) = h(u) \cdot h(v)
>$$
>where the *group operation* on the *left side* of the equation is that *of* $G$ and on the *right side* that *of* $H.$

>[!important]
>From this property, one can deduce that
>- $h$ maps the *identity element* $1_{G}$ of $G$ to the *identity element* $1_{H}$ of $H$,
>  $$
>  h(1_{G}) = 1_{H}
> $$
>- $h$ also maps *inverses* to *inverses* in the sense that for any $a \in G$
>$$
>h(a^{-1}) = (h(a))^{-1}
>$$

>[!important]
>Hence one can say that a **homomorphism** $h$ "is **compatible with the group structure**".

## Explanation

>[!important]
>A **homomorphism** is a map between **two algebraic structures** of *the same type* (that is of the same name), that **preserves the operations** of the structures.

>[!important]
>A homomorphism **not necessarily need** to be bijective.

## Variations

>[!important]
>An **injective** *group homomorphism* is [[Monomorphism between Groups]]

- [[Injective Function]]

>[!important]
>An **surjective** *group homomorphism* is [[Epimorphism between Groups]]

- [[Surjective Function]]

>[!important]
>A **bijective** *group homomorphism* is [[Isomorphism between Groups]] 

- [[Bijective Function and Inverse Function]]

>[!important]
>A *group homomorphism* between $G$ **itself** is [[Endomorphism between Groups]]

>[!important]
>A *group homomorphism* between $G$ **itself** and is **bijective** is [[Automorphism between Groups]]

- [[Bijective Function and Inverse Function]]






-----------
##  Recommended Notes and References

- [[Group]]
- [[Homomorphism between Rings]]
- [[Lie Algebra Homomorphism]]
- [[Bundle Homomorphism]]
- [[Graph Homomorphism]]

- [[Abstract Algebra by Dummit]]