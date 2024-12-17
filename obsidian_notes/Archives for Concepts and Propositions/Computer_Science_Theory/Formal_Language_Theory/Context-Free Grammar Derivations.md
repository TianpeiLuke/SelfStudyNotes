---
tags:
  - concept
  - complier_theory/parsing
  - computational_linguistic/parsing
  - computer_science/context_free_language
  - computational_linguistic/context_free_language
keywords:
  - context_free_grammar_derivations
topics:
  - computer_science/context_free_grammar
  - computational_linguistic/context_free_language
name: Context-Free Grammar Derivations
date of note: 2024-12-14
---

## Concept Definition

>[!important]
>**Name**: Context-Free Grammar Derivations

![[Formal Grammar Abstract Definition#^d2e40a]]

![[Context-Free Grammars#^7bce3b]]

### Derivation of CFG

![[Sentential Form in Formal Grammar#^d8e2f9]]

![[Derivation from Formal Grammar#^b3735b]]

>[!important] Definition
>Let $G=(\Sigma, V, S, P)$ be a *context-free grammar*, and $w, z$ be two *sentential forms* of $G$
>
>The **derivation** from **context-free grammar** using $p$ is denoted as $$w \stackrel{p}{\implies} z$$

- [[Formal Grammar Abstract Definition]]
- [[Context-Free Grammars]]
- [[Sentential Form in Formal Grammar]]
- [[Derivation from Formal Grammar]]

### Leftmost and Rightmost Derivations

>[!important] Definition
>A **leftmost derivation** is a derivation that *at each step*, we *replace* the *leftmost variable* by one of its *production bodies*. $$\alpha\,A\,B\,\beta \underset{lm}{\implies} \alpha\,\gamma\,B\,\beta$$
>- The **leftmost direct derivation** is denote as $$w \underset{lm}{\implies} z$$
>- The **leftmost multi-step derivation** is denoted as $$w  \stackrel{*}{\underset{lm}{\implies}} z$$


>[!important] Definition
>A **rightmost derivation** is a derivation that *at each step*, we *replace* the *rightmost variable* by one of its *production bodies*. $$\alpha\,A\,B\,\beta \underset{rm}{\implies} \alpha\,A\,\gamma\,\beta$$
>- The **leftmost direct derivation** is denote as $$w \underset{rm}{\implies} z$$
>- The **leftmost multi-step derivation** is denoted as $$w  \stackrel{*}{\underset{rm}{\implies}} z$$


## Explanation


- [[Parse Tree or Derivation Tree in Context-Free Grammar]]


-----------
##  Recommended Notes and References




- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 176 -  178,