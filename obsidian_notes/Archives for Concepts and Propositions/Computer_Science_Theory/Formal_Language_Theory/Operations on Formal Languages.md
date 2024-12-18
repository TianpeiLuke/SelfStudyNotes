---
tags:
  - concept
  - computer_science/formal_language
  - computer_science/regular_expression
keywords:
  - union_language
  - concatenation_language
  - closure_language
  - kleene_star_language
topics:
  - computer_science/formal_language
  - computer_science/regular_expression
name: Operations on Formal Languages
date of note: 2024-12-17
---

## Concept Definition

>[!important]
>**Name**: Operations on Formal Languages

### Operations of Regular Expression

![[Formal Language Abstract Definition#^820f46]]

>[!important] Definition
>The three *operations* on **languages** are defined as follows:
>- **Union operation**: the union of two languages $$L \cup M := \left\{ s:\; s\in L \lor s \in M \right\} $$ is the set of strings that are either in $L$ or $M$
>- **Concatenation operation**: the *concatenation* of two languages $$L \cdot M := LM := \left\{ st:\; s\in L \land t\in M \right\} $$
>	- the empty string $\epsilon$ is **identity** for *concatanation operation* $$L\{\epsilon\} = \{\epsilon\} L = L$$
>	- $$L^i := \left\{ \sigma_{1}\sigma_{2}\,{}\ldots{}\,\sigma_{i}: \; \sigma_{j} \in L   \right\}$$ is the concatenation of $i$ copies of $L$
>- **Kleene star operation** or **Kleene closure** or **star** or **closure operation** of a language $L$ is defined as $$L^{*} := \left\{ \sigma_{1}\sigma_{2}\,{}\ldots{}\,: \; \sigma_{i} \in L   \right\} := \bigcup_{i \ge 0}L^{i} $$  which is the set of strings that can be formed by taking *any number of strings* from $L$ (possibility with *repetition*) and *concatenating* all of them.

^f9ecd3


- [[Group]]
- [[Alphabets and Strings Abstract Definition]]
- [[Formal Language Abstract Definition]]

### Regular Expression via Algebraic Structure

![[Regular Expression Definition#^697bd7]]

- [[Regular Expression Definition]]


## Explanation





-----------
##  Recommended Notes and References

- [[Regular Expression Definition]]


- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 86 - 87