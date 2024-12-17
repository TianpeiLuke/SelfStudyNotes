---
tags:
  - concept
  - natural_language_processing/word
  - computer_science/context_free_language
  - computer_science/finite_automata
  - computational_linguistic/language
  - computer_science/formal_language
  - complier_theory
keywords:
  - strings_formal_language
  - formal_language
  - formal_grammar
topics:
  - computational_linguistic/language
  - computer_science/formal_language
name: Derivation from Formal Grammar
date of note: 2024-12-15
---

## Concept Definition

>[!important]
>**Name**: Formal Grammar Abstract Definition

![[Alphabets and Strings Abstract Definition#^339899]]

![[Formal Language Abstract Definition#^820f46]]

![[Formal Grammar Abstract Definition#^d2e40a]]

- [[Formal Grammar Abstract Definition]]
- [[Formal Language Abstract Definition]]
- [[Alphabets and Strings Abstract Definition]]

![[Sentential Form in Formal Grammar#^d8e2f9]]

- [[Sentential Form in Formal Grammar]]

>[!important] Definition
>Let $G=(\Sigma, V, S, P)$ be a *grammar*, and $w, z$ be two *sentential forms* of $G$
>- If we apply a *production* $p\in P$ to a *string* of symbols $$w\in (\Sigma \cup V)^{*}\;V\;(\Sigma \cup V)^{*}$$ to yield a new string $$z\in (\Sigma \cup V)^{*},$$ we say that $w$ **directly derives** $z$ *using* $p$, denoted as $$w \stackrel{p}{\implies} z$$
>- We say that $w$ **derives** $z$ i.e. $$w \stackrel{*}{\implies} z$$  if there exists a *sequence* of *sentential forms* $\sigma_{1}\,{,}\ldots{,}\,\sigma_{n}$ such that $$w \implies \sigma_{1} \,{\implies}\ldots{\implies}\,\sigma_{n} \implies z.$$
>- The derivatoin operation $\implies$ defines  the process of *deriving* strings by *applying productions* from *head* to *body*.	

^b3735b

>[!info]
>Note that we use $\to$ to represent the **production rule**. .e.g $$A \to \gamma$$
>
>And we use $\implies$ to represent the **derivation** of *grammar* $$\alpha A \beta \implies \alpha\,\gamma\,\beta$$

## Explanation

>[!quote]
>We apply the **productions** of a **CFG** to infer that certain strings are *in the language* of a certain variable. 
>
>There are two approaches to this inference.
>- The more conventional approach is to use the **rules** from *body to head*. 
>	- That is we take strings known to be in the language of each of the *variables* of the body, *concatenate* them, in the proper *order*, with any *terminals* appearing in the *body* and infer that the resulting string is in the language of the variable in the *head*.
>	- We shall refer to this procedure as **recursive inference**. 
>- There is another approach to defining the language of a grammar in which we use the **productions** from *head to body*.
>	- We *expand* the start symbol using one of its productions (i.e using a production whose *head* is the *start symbol*).
>	- We further *expand* the resulting string by *replacing* one of the variables by the body of one of its productions, and so on, *until* we derive a string consisting *entirely of terminals*.
>	- The **language of the grammar** is all strings of terminals that we can obtain in this way. This use of grammars is called **derivation.**
>	  
>-- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 175	  

- [[Membership Problem in Automata Theory]]
- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]
- 


## Parsing and Derivation in Context-Free Grammar

- [[Context-Free Grammars or CFG]]
- [[Context-Free Grammar Derivations]]
- [[Context-Free Language]]

- [[Parse Tree or Derivation Tree in Context-Free Grammar]]



-----------
##  Recommended Notes and References


- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp  28 - 30
- [[Handbook of Natural Language Processing by Indurkhya]] pp 65
- [[Foundations of Machine Learning by Mohri]]
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Speech and Language Processing by Jurafsky]] pp 392
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 83

- [Stanford cs143](https://web.stanford.edu/class/archive/cs/cs143/cs143.1128/handouts/080%20Formal%20Grammars.pdf)
- [UCR CS215](https://www.cs.ucr.edu/~jiang/cs215/tao-new.pdf)
