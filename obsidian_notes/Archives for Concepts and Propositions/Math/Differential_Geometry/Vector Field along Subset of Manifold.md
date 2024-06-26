---
tags:
  - concept
  - math/differential_geometry
keywords:
  - vector_field
topics:
  - differential_geometry
name: Vector Field along Subset of Manifold
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Vector Field along Subset of Manifold

>[!important] Definition
>If $M$ is a smooth manifold with or without boundary and $A \subseteq M$ is an arbitrary *subset*.
>
 >A **vector field along $A$** is a *continuous map* $X: A \rightarrow TM$ satisfying $$\pi \circ X = \text{Id}_A,$$ 
 >or in other words $X_p \in TpM$  for each $p \in A$. 

>[!important] Definition
>We call it a **smooth vector field along $A$** if for each $p \in A$, there is a *neighborhood* $V$ of $p$ in $M$ and a *smooth vector field* $\widetilde{X}$ on $V$ that **agrees with $X$** on $V \cap A$.

- [[Vector Field on Manifold]]
- [[Smooth Vector Field on Manifold]]



## Explanation

>[!important] Extension Lemma for Vector Fields
>Let $M$ be a smooth manifold with or without boundary, and let $A \subseteq M$ be a **closed subset.** Suppose $X$ is a **smooth vector field along $A$.** 
 >
 >Given any open subset $U$ containing $A$, there **exists** a **smooth global vector field** $\widetilde{X}$ on $M$ such that $$\widetilde{X}|_{A} = X$$ and $$\text{supp}\,\widetilde{X} \subseteq U.$$

- [[Hahn-Banach Theorem]]

>[!info]
>As an important special case, **any vector at a point** can be **extended** to a **smooth vector field** on the **entire manifold**.

>[!important] Proposition 
>Let $M$ be a smooth manifold with or without boundary. Given $p \in M$ and $v \in T_{p}M$, there *exists* a **smooth global vector field** $X$ on $M$ such that $$X_p  = v.$$




-----------
##  Recommended Notes and References

- [[Vector Field on Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Tangent Bundle]]


- [[Introduction to Smooth Manifolds by Lee]]