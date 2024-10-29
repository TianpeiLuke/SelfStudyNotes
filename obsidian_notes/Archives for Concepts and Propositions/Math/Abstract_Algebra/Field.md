---
tags:
  - concept
  - math/abstract_algebra
keywords:
  - field_algebra
topics:
  - algebra
name: Field
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Field

>[!important] Definition
>A **field** is a **commutative division ring**.

- [[Commutative Ring]]
- [[Division Ring]]

>[!important] 
>In specific, a **field** $F$ is a set together with two operations: *addition* $+: F \times F\to F$ and *multiplication* $\times: F \times F\to F$ that satisfy the following axioms
>- $(F, +)$ is an **abelian group**. 
>  That is, the *addition* $+: F\times F\to F$ satisfying 
>	- **Associativity for addition**: for all $a, b, c \in F$, $$(a + b) + c = a + (b + c)$$
>	- **Zero element**: there exists an element $0 \in F$, such that $$0 + a = a + 0 = a$$ for all $a\in F.$
>	- **Negative element:** for every $a\in F$, there exists $-a \in F$ such that $$a + (-a) = 0$$, where $0\in F$ is the zero element in $F$.
>	- **Commutativity for addition**: for all $a, b\in F,$ $$a + b = b + a.$$
>- $(F, \times)$  is an **abelian group** as well.
>  That is, the *multiplication* $\times: F\times F \to F$ satisfying
>	- **Associativity for multiplication** . That is, for all $a, b, c \in R$, $$(a \times  b) \times c = a \times (b \times c)$$
>	- **Identity element**: there exists an element $1 \in F$ and $1\neq 0$ such that $1 \times a = a \times 1 = a$ for all $a\in F.$
>	- **Multiplicative Inverse element**: for every $a \in F$, there exists $a^{-1} \in F$ such that $a \times a^{-1} = a^{-1} \times a = 1.$ 	  	  
>	- **Commutativity for multiplication**: for all $a, b\in F,$ $$a \times b = b \times a.$$
>- **Distributivity**: for all $a, b, c\in R$, 
>  $$
>  (a + b) \times c = a\times c + b \times c
> $$ 
> and
>  $$
>  a \times (b + c) = a\times b + a \times c.
> $$ 

- [[Abelian Group]]

## Explanation





-----------
##  Recommended Notes and References

- [[Commutative Ring]]
- [[Division Ring]]
- [[Ring]]

- [[Abelian Group]]

- [[Vector Space over a Field]]

- [[Abstract Algebra by Dummit]]