---
tags:
  - concept
  - math/abstract_algebra
keywords:
  - ring_algebra
topics:
  - algebra
name: Ring
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Ring

>[!important] Definition
>A **ring** $R$ is a set together with two *binary operations* $+$ and $\times$ (called **addition** and **multiplication**) satisfying the following axioms:
>- $(R, +)$ is an **abelian group**. 
>  That is, the *addition* $+: R\times R\to R$ satisfying 
>	- **Associativity for addition**: for all $a, b, c \in R$, $$(a + b) + c = a + (b + c)$$
>	- **Zero element**: there exists an element $0 \in R$, such that $$0 + a = a + 0 = a$$ for all $a\in R.$
>	- **Negative element:** for every $a\in R$, there exists $-a \in R$ such that $$a + (-a) = 0$$, where $0\in R$ is the zero element in $R$.
>	- **Commutativity for addition**: for all $a, b\in R$, $$a + b = b + a.$$
>- The *multiplication* $\times: R\times R \to R$ is **associative** . That is, for all $a, b, c \in R$, $$(a \times  b) \times c = a \times (b \times c)$$
>- **Distributivity**: for all $a, b, c\in R$, 
>  $$
>  (a + b) \times c = a\times c + b \times c
> $$ 
> and
>  $$
>  a \times (b + c) = a\times b + a \times c.
> $$ 

- [[Abelian Group]]
- [[Group]]
- [[Binary Operation on Set]]

## Explanation





-----------
##  Recommended Notes and References


- [[Polynomial Ring]]
- [[Matrix Ring]]

- [[Commutativity and Anticommutativity of Matrices]]
- [[General Linear Group]]
- [[Group]]

- [[Abstract Algebra by Dummit]]