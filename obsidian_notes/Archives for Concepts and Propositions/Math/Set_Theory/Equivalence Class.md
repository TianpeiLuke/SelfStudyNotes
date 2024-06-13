---
tags:
  - concept
  - math/set_theory
keywords:
  - equivalence_class
topics:
  - set_theory
name: equivalence class
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Equivalence Class

>[!important] Definition
>Let $R: X \times X$ is an *equivalence relation.*
>
>The **equivalence class** of an element $x$ is denoted as $$[x] := \set{y \in X:  xRy}.$$ 

- [[Equivalence Relation]]


## Explanation

>[!important]
>Since $x \sim y \Rightarrow y \in [x]$, we see that if $[x] \neq [y]$, then $x \not\sim y$, i.e. **representative** of **different equivalence classes** are **not in** the given relationship.

>[!info]
>In other words, 
>- for every $x\in X$, $x\in [y]$ for some $y\in X.$
>- $[a] \cap [b] = \emptyset$ if $(a, b) \not\in R.$
>- $$\bigcup_{x\in X}[x] = X.$$
>
>The *set of equivalence classes* provides **a partition of the set $X$** in that every $z \in X$ can *must* belong to **only one equivalence class** $[x]$. 

  


-----------
##  Recommended Notes and References

- [[Relation]]
- [[Topology Book by Munkres]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]