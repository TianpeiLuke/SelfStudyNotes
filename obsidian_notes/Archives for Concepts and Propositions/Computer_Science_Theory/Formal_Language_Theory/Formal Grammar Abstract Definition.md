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
name: Formal Grammar Abstract Definition
date of note: 2024-12-15
---

## Concept Definition

>[!important]
>**Name**: Formal Grammar Abstract Definition

![[Alphabets and Strings Abstract Definition#^339899]]

![[Formal Language Abstract Definition#^820f46]]

>[!important] Definition
>**Formal grammar** is a _formal_ system that defines a set of *rules* for generating *valid strings* within a *language*.
>
>A **formal grammar** is a quadruple $$(\Sigma, V, S, P)$$ where
>- $\Sigma$ is a *finite* nonempty set called the **terminal alphabet**.
>	- The elements of $\Sigma$ are called the **terminals.**
>- $V$ is a *finite* nonempty set called  the  **non-terminal alphabet**.  
>	- The elements of $V$ are called the **variables** or **non-terminals.**
>- $S\in V$ is a distinguished *non-terminal* called the **start symbol**.
>- $P$ is a *finite* set of **productions** or **rules** of the form $$\alpha \to \beta$$ where
>	- $$\alpha \in (\Sigma \cup V)^{*}\;V\;(\Sigma \cup V)^{*}$$ is a *string* of *terminals* and *non-terminals* containing *at least one non-terminal*
>	- $$\beta \in (\Sigma \cup V)^{*}$$  is a *string* of *terminals* and *non-terminals*. 

^d2e40a

- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 261
- [[Membership Problem in Automata Theory]]
- [[Formal Language Abstract Definition]]
- [[Alphabets and Strings Abstract Definition]]

![[Derivation from Formal Grammar#^b3735b]]

- [[Derivation from Formal Grammar]]


>[!important] Definition
>- **grammar**: 
>	- a set of *rules* by which *valid* sentences in a *language* are constructed.
>- **non-terminal**: 
>	- a grammar *symbol* that can be *replaced/expanded* to a sequence of symbols.
>- **terminal**:
>	- an *actual word* in a language; these are the symbols in a grammar that *cannot be replaced* by anything else. 
>- **production**: 
>	- a grammar *rule* that describes how to *replace/exchange symbols*.
>	- A general form of a *production* for *non-terminal* is $$X \to Y_{1}Y_{2}\,{}\ldots{}\,Y_{n}$$ where $X$ is declared as *equivalent* to the *concatenation* of symbols $Y_{1}Y_{2}\,{}\ldots{}\,Y_{n}$.
>		- Thus each $X$ may be replaced by the string $Y_{1}Y_{2}\,{}\ldots{}\,Y_{n}$.
>- **sentence**:
>	- For each non-terminals, we can use a *production* to *replace/expand* with a concatenation of symbols. 
>	- A *sentence* is a *finished string of terminals*.
>- **derivation**:
>	- a *sequence* of applications of the *rules* of a grammar that produces a *finished string of terminals*
>	- A **derivation** of a sentence $\gamma$ is given by $$S \to \sigma_{1} \,{\to}\ldots{\to}\,\sigma_{k} \to \gamma$$
>- **start symbol**: a grammar has a *single non-terminal* from which *all sentences* derive.

- [Stanford cs143](https://web.stanford.edu/class/archive/cs/cs143/cs143.1128/handouts/080%20Formal%20Grammars.pdf)
- [UCR CS215](https://www.cs.ucr.edu/~jiang/cs215/tao-new.pdf)



## Explanation







## Formal Grammar

### Regular Language

- [[Regular Expression Definition]]
- [[Regular Expression Properties]]

### Context-Free Language

![[Context-Free Grammars#^7bce3b]]

- [[Context-Free Grammars]]
- [[Context-Free Grammar Derivations]]
- [[Backus–Naur Form or BNF]]



-----------
##  Recommended Notes and References


- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 173
- [[Artificial Intelligence Modern Approach by Russell]]
- Wikipedia [Formal_grammar](https://en.wikipedia.org/wiki/Formal_grammar)