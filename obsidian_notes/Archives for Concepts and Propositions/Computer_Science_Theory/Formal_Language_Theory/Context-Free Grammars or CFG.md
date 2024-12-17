---
tags:
  - concept
  - natural_language_processing
  - computational_linguistic/constituency_grammar
  - computer_science/context_free_language
keywords:
  - context_free_grammar
topics:
  - computer_science/formal_language
  - computational_linguistic/language
name: Context-Free Grammars or CFG
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Context-Free Grammars or CFG

![[Formal Grammar Abstract Definition#^d2e40a]]

- [[Formal Grammar Abstract Definition]]

>[!important] Definition
>The **context-free grammar (CFG)** is a *formal grammar* in which the *left-hand side* of each *production* rule consists of *only a single nonterminal symbol*.
>
>A *formal grammar* $$G := (\Sigma, V, S, P)$$ is called **context-free grammar** if each *production* $p\in P$ is of the form $$A \stackrel{p}{\to} \alpha$$ where 
>- $A\in V$ is a *single non-terminal symbol* 
>- and $\alpha\in (\Sigma \cup V)^{*}$ is a *string* of *terminal or non-terminal* (including *empty string* $\epsilon$)
>- That is $$P \subset V \times (\Sigma \cup V)^{*}.$$

^7bce3b

- [[Alphabets and Strings Abstract Definition]]
- [[Sentential Form in Formal Grammar]]
- [[Relation]]


>[!important] Definition
>It is convenient to think of a **production** as *belonging to* the *variable of its head*. 
>- We shall often use remarks like the **productions for $A$** or **$A$-productions** to refer to the productions $p\in P$ whose head is variable $A$ $$A \stackrel{p}{\to} \gamma$$  
>- We may write the *productions for a grammar* by listing each variable once and then *listing all the bodies* of the productions for that variable separated by *vertical bars*. 
>	- That is the productions $$A \to \alpha_{1},\, A \to \alpha_{2} \,{,}\ldots{,}\, A \to \alpha_{n}$$ can be replaced by the notation $$A \to \alpha_{1}\,|\,\alpha_{2}\,{|}\ldots{|}\, \alpha_{n}.$$


## Explanation

>[!info]
>**Regardless** of the **symbols around it (context)**, each *non-terminal symbol* $A$ can be replaced by a *string*. $$A \to \alpha$$



>[!info]
>The **context-sensitive grammar** has production rules of the form $$\alpha\,A\,\beta \to \alpha\,\gamma\,\beta$$

## Derivation and Language of Context-Free Grammar

- [[Context-Free Grammar Derivations]]
- [[Context-Free Language]]



-----------
##  Recommended Notes and References


- [[Strong and Weak Grammar Equivalence]]
- [[Chomsky Normal Form as Grammatical Simplification]]


- [[Speech and Language Processing by Jurafsky]]  pp 392
- [[Handbook of Natural Language Processing by Indurkhya]]
- [[Foundations of Statistical Natural Language Processing by Manning]]
- [[Algorithm Design Manual by Skiena]] pp 687
- [[Foundations of Machine Learning by Mohri]] pp 363
- [[Artificial Intelligence Modern Approach by Russell]] pp 1060, 889, 918, 919
- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 171, 173
- Wikipedia [Context-free_grammar](https://en.wikipedia.org/wiki/Context-free_grammar)