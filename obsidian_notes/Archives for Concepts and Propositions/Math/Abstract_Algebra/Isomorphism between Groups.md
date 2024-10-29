---
tags:
  - concept
  - math/abstract_algebra
keywords:
  - group_isomorphism
topics:
  - algebra
name: Isomorphism between Groups
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Isomorphism between Groups

>[!important] Definition
>Given two *groups*, $(G,∗)$ and $(H,\cdot)$, a **group isomorphism** from $(G,∗)$ to $(H,\cdot)$ is a **bijective** *group homomorphism*. 
>
>That is, for a *group isomorphism* $h: (G,∗) \to (H,\cdot)$, there exists an *inverse* $$h^{-1}: (H,\cdot) \to (G,∗)$$ that is also a *group isomorphism*.
>
>We say $G$ and $H$ are **isomorphic** to each other.
>$$
>G \simeq H.
>$$

>[!important]
>That is, for all $x, y \in H$
>$$
>h^{-1}(x \cdot y) = h^{-1}(x) * h^{-1}(y)
>$$

>[!info]
>It is easy to see that 
>$$
>(h\circ h^{-1})(x \cdot y) = h(h^{-1}(x \cdot y) ) = h(h^{-1}(x) * h^{-1}(y)) = h(h^{-1}(x)) \cdot h(h^{-1}(y)) = x \cdot y
>$$

- [[Homomorphism between Groups]]
- [[Bijective Function and Inverse Function]]


## Explanation

>[!important]
>A **group isomorphism** is both a **group monomorphism** and a **group epimorphism** 

- [[Monomorphism between Groups]]
- [[Epimorphism between Groups]]



-----------
##  Recommended Notes and References

- [[Homomorphism between Groups]]
- [[Group]]

- [[Homeomorphism]]
- [[Diffeomorphism]]
- [[Linear Isomorphism]]
- [Homomorphism between Groups](app://obsidian.md/Homomorphism%20between%20Groups)
- [[Isometry and Isometric isomorphism]]
