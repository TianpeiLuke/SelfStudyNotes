---
tags:
  - concept
  - math/algebra
  - math/linear_algebra
keywords:
  - left_r_module
  - module
topics:
  - algebra
  - linear_algebra
name: Left Ring Module
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Left Ring Module

>[!important] Definition
>Let $R$ be a *ring* (*not necessarily commutative nor with $1$*). 
>
>A **left $R$-module** or a **left module over ring $R$** is a set $M$ together with 
>- a binary operation $+: M \times M \to M$ under which $M$ is an **abelian group**.
>  That is, the *addition* $+: M\times M\to M$ satisfying 
>	- **Associativity for addition**: for all $m, n, p \in M$, $$(m + n) + p = m + (n + p)$$
>	- **Commutativity for addition**: for all $m, n\in M,$ $$m + n = n + m.$$	  
>	- **Identity of addition**: there exists an element $0 \in M$, such that $$0 + a = a + 0 = a$$ for all $a\in M.$
>	- **Inverse of addition:** for every $a\in M$, there exists $-a \in M$ such that $$a + (-a) = 0,$$ where $0\in M$ is the zero element for addition in $M$.
>	  
>- an **action** of $R$ **on** $M$, that is, a map $\cdot: R \times M \to M$, for all $r\in R$ and for all $m\in M$, which satisfies
>	- **Compatibility** of *action* with *ring multiplication*: 
>	  That is, for all $r, s\in R$ and $m \in M$, $$(r\cdot s) \cdot m = r \cdot (s \cdot m)$$
>	- **Distributivity** of *action* with respect to *addition* in $M$: 
>	  That is, for all $r\in R$	and $m, n \in M$, $$r\cdot (m + n) = r\cdot m + r \cdot n$$  
>	- **Distributivity** of *action* with respect to *ring addition*:
>	  That is, for all $r, s\in R$ and $m\in M$, $$(r+s) \cdot m = r \cdot m + s \cdot m.$$  

- [[Group Action]]
- [[Abelian Group]]
- [[Ring]]

>[!important] Definition
>If the ring $R$ has *identity* $1$, we impose additional axiom
>- for all $m \in M$, 
>$$
>1 \cdot m = m.
>$$

- [[Ring with Identity]]

## Explanation





-----------
##  Recommended Notes and References


- [[Ring]]
- [[Abelian Group]]
- [[Group Action]]

- [[Vector Space over a Field]]

- [[Abstract Algebra by Dummit]]