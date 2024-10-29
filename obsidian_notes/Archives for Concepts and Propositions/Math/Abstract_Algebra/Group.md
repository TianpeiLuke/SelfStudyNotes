---
tags:
  - concept
  - math/abstract_algebra
keywords:
  - group_algebra
topics:
  - algebra
  - abstract_algebra
name: Group
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Group

>[!important] Definition
>A **group** is a set $G$ with a **binary operation** $\cdot: G \times G \to G$ (usually called **multiplication**), denoted $a \cdot b = ab$, such that the following properties are satisfied:
>- **Associativity**: for all $a, b, c \in G$, 
>  $$
>  (a \cdot b) \cdot c = a \cdot (b \cdot c)
> $$
>- **Identity element**: there exists an element $e \in G$ such that  for any $a \in G$, 
>  $$
>  e \cdot a = a \cdot e = a
> $$
>Note that by above definition, such element $e$ is **unique**, called the **identity element** of the group. We denote it as $1$.
>- **Inverse element**: for every $a \in G$, there exists an element $b \in G$ such that 
>$$
>a \cdot b = b \cdot a = 1
>$$
>where $1 \in G$ is the identity element. 
>
>For each $a\in G$, such $b\in G$ as described above is **unique**, called the **inverse** of $a$ in the group. We denote it as $a^{-1}.$

- [[Binary Operation on Set]]

## Explanation





-----------
##  Recommended Notes and References

- [[Set Operations]]


- [[Abstract Algebra by Dummit]]