---
tags:
  - concept
  - natural_language_processing/regular_expression
  - computer_science/regular_expression
keywords:
  - regular_expression
  - kleene_operation
topics:
  - natural_language_processing/regular_expression
  - computer_science/regular_expression
name: Regular Expression Algebraic Definition
date of note: 2024-12-14
---

## Concept Definition

>[!important]
>**Name**: Regular Expression Algebraic Definition

### Operations on Languages

![[Operations on Formal Languages#^f9ecd3]]

- [[Operations on Formal Languages]]

### Regular Expression as Algebraic Group

![[Regular Expression Definition#^697bd7]]

- [[Regular Expression Definition]]

### Algebraic Properties of Operations

>[!important] Proposition
>The set of all **regular expressions** over some alphabet $\Sigma$,  equipped with the *union operation* $+$ and *concatenation operation* $\cdot$, forms a **idempotent semi-ring** $$(\mathcal{R}, +, \cdot)$$
>
>Specifically, 
>- $(\mathcal{R}, +)$ is an **abelian group**. 
>  That is, the *union* $$+: \mathcal{R}\times \mathcal{R}\to \mathcal{R}$$ is *closed* in $\mathcal{R}$, and it satisfies the following properties 
>	- **Associativity for union**: for all $E, F, G \in \mathcal{R}$, $$(E + F) + G = E + (F + G)$$
>	- **Identity element (empty set)**: there exists an element $\emptyset \in \mathcal{R}$, such that for all $L\in \mathcal{R},$ $$\emptyset + L = L + \emptyset = L$$ 
>	- **Commutativity for union**: for all $E, F\in \mathcal{R}$, $$E + F = F + E.$$
>	- **Idempotent for union**, i.e., for any $L\in \mathcal{R}$, $$L + L = L$$ 
>- The *concatenation* $$\cdot: \mathcal{R}\times \mathcal{R} \to \mathcal{R}$$ satisfies the following properties: 
>	- **Associativity for concatenation**:  for all $E, F, G \in \mathcal{R}$, $$(E \cdot  F) \cdot G = E \cdot (F \cdot G)$$
>	- **Identity element (empty string)**: there exists $\epsilon\in \mathcal{R}$ such that for all $L\in \mathcal{R}$, $$\epsilon \cdot L = L \cdot \epsilon = L$$
>	- **Annihilator element (empty set)** : there exists $\emptyset \in \mathcal{R}$ such that  for all $L\in \mathcal{R}$, $$\emptyset \cdot L = L \cdot \emptyset = \emptyset$$ 
>- **Distributivity**: for all $E, F, G\in \mathcal{R}$, 
>  $$
>  (E + F) \cdot G = E \cdot G + F \cdot G
> $$ 
> and
>  $$
>  E \cdot (F + G) = E \cdot F + E \cdot G.
> $$ 

^df3a11

- [[Alphabets and Strings Abstract Definition]]
- [[Semi-Ring]]
- [[Set Operations]]

### Property of Closure / Star Operation

>[!important] Proposition
>Let $\mathcal{R}$ be the set of all **regular expressions** over some alphabet $\Sigma$,  equipped with the *star operation* $*$.
>
>Then the *star operation* satisfies the following properties:
>- **Idempotence**:  for all $L\in \mathcal{R}$  $$(L^{*})^{*} = L^{*}$$ 
>- **Closure** of **empty set** is an **empty string** i.e. $$(\emptyset)^{*} = \epsilon$$
>- Define $$L^{+} := L + LL \,{+}\ldots{+}\,$$ and $$L^{*} := \epsilon + L + LL \,{+}\ldots{+}\,$$ Then 
>	- $$L^{+} = L\,L^{*} = L^{*}\,L$$
>	- $$L^{*} = L^{+} + \epsilon$$
>

^3659de


- [[Closed Convex Function and Closure Operation]]

### Kleene Algebra

>[!important] Definition
>The **Kleene algebra** is an *idempotent* (and thus partially ordered) *semi-ring* endowed with a *closure operator* $*$ 
>$$(\mathcal{R}, +, \cdot, *)$$
>- The set of all *regular expressions* forms a *Kleene algebra.*

- WIkipedia [Kleene_algebra](https://en.wikipedia.org/wiki/Kleene_algebra)


## Explanation




-----------
##  Recommended Notes and References



- [[Formal Language Abstract Definition]]
- [[Mathematical Induction]]

- [[Ring with Identity]]
- [[Group]]

- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 115 - 122


