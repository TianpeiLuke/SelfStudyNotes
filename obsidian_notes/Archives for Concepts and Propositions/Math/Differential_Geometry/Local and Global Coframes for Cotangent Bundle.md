---
tags:
  - concept
  - math/differential_geometry
keywords:
  - local_frame
  - global_frame
topics:
  - differential_geometry
name: Local and Global Coframes for Cotangent Bundle
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Local and Global Coframes for Cotangent Bundle

>[!important] Definition
>Let $M$ be a smooth manifold with or without boundary, and let $U \subseteq M$ be an open subset.
>
 >A **local coframe** for $M$ over $U$ is an *ordered $n$-tuple* of *covector fields* $$(\epsilon^1, \ldots, \epsilon^n)$$ defined on $U$ such that $$(\epsilon^{i}|_{p})$$ *forms a basis* for $T_{p}^{*}M$ at each point $p \in U$. 
 >
 >If $U = M$, it is called a **global coframe**. (A *local coframe* for $M$ is just a *local frame* for *the vector bundle* $T^{*}M$


- [[Linear Independence]]
- [[Basis of Vector Space]]
- [[Space of all Smooth Covector Fields on a Manifold]]


## Explanation


## Example

>[!example]
>For any smooth chart $(U, (x^i))$, the **coordinate covector fields** $$(\lambda^i)$$ defined above *constitute* *a local coframe* over $U$, called **a coordinate coframe**. 
>
>Every coordinate frame is **smooth**, because its **component functions** in the given chart are **constants**.
>
>[[Coordinate Representation of Differential]] suggests that we represent the coordinate covector fields as the differential of coordinate function
>$$(dx^i)$$




-----------
##  Recommended Notes and References

- [[Local and Global Frames for Vector Bundle]]

- [[Space of all Smooth Covector Fields on a Manifold]]
- [[Cotangent Bundle]]





- [[Introduction to Smooth Manifolds by Lee]]