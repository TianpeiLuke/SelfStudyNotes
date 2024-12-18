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
name: Regular Expression Definition
date of note: 2024-12-14
---

## Concept Definition

>[!important]
>**Name**: Regular Expression Definition

### Operations on Languages

![[Operations on Formal Languages#^f9ecd3]]

- [[Operations on Formal Languages]]

### Regular Expression as Algebraic Group

>[!important] Definition
>Let $\Sigma$ be an alphabet.
>- For each **regular expression** $E$, let $L(E)$ be the **language** it represents.
>
>The **regular expression** can be defined *recursively* as follows:
>- **Basic**
>	- The *constant* $\epsilon$, and $\emptyset$ are *regular expressions*.
>		- The corresponding languages are denoted as $$L(\epsilon) := \{ \epsilon \}, \quad L(\emptyset) = \emptyset.$$
>	- If $a\in \Sigma$ is any symbol, then the *literal charater* $a$ is a *regular expression*
>		- The corresponding languages is denoted as $$L(a) := \{ a \}.$$
>	- A variable $L \in V$ is a variable *representing any language*
>		- We use capitalized and italic symbols
>- **Induction**:
>	- If $E, F$ are *regular expression*, then $$E + F\; \text{ or }\; E|F$$ is *regular expression*, denoting the **union** of $L(E)$ and $L(F)$ i.e. $$L(E + F) = L(E) \cup L(F)$$
>	- If $E, F$ are *regular expression*, then $$E\,F$$ is a *regular expression*, denoting the **concatenation** of $L(E)$ and $L(F)$ i.e. $$L(E\,F) = L(E) \, L(F)$$
>	- If $E$ is a *regular expression*, then the **Kleene star/closure operation** $$E^{*}$$ is a *regular expression*, denoting the **closure** of $L(E)$, i.e. $$L(E^{*}) = \left(L(E)\right)^{*}$$
>	- If $E$ is a *regular expression*, then the **parenthesized** $E$ $$(E)$$ is a *reguler expression*, denoting the **same language** as $E$, i.e. $$L((E)) = L(E).$$

^697bd7

- [[Alphabets and Strings Abstract Definition]]
- [[Formal Language Abstract Definition]]
- [[Mathematical Induction]]

### Ordering of Operations in Regular Expression

>[!important] 
>For **regular expression**, the following is the the **order of preceduence** for operators:
>1. The **Kleene star operator** is of *highest precedence*:
>	- It applies only to *smallest sequence* of symbols to its *left* that is a well-formed *regular expression* $$\alpha\,\beta^{*} = \alpha \left(\beta^{*}\right)$$
>2. The second highest is the **concatenation operation** or *dot operation*
>	- All expressions that are **juxtaposed (adjacent without intervening operator)** are grouped together
>	- The concatenation is *associative* $$\alpha \cdot (\beta \cdot \gamma) = (\alpha \cdot \beta) \cdot \gamma$$
>	- *After grouping* all *stars* to their operands, we group the concatenation operations and their operands $$\gamma \cdot \alpha \cdot \beta^{*} = \gamma \cdot (\alpha \cdot (\beta^{*}))$$
>3. The last is the **union operator** 
>	- All unions are the last to be grouped together with their operands.
>	- *union* is *associative* too $$\alpha + (\beta + \gamma) = (\alpha + \beta) + \gamma$$
>	- e.g. $$\alpha\cdot \beta^{*} + \gamma = (\alpha \cdot (\beta^{*})) + \gamma$$
>	



### Algebraic Properties of Operations

![[Regular Expression Algebraic Definition#^df3a11]]

![[Regular Expression Algebraic Definition#^3659de]]

- [[Regular Expression Algebraic Definition]]
- [[Semi-Ring]]


## Explanation

>[!quote]
>Strictly speaking, a **regular expression** $E$ is just an **expression** *not* a **language**.
>-  We should use $$L(E)$$ when we want to refer to the *language* that $E$ denotes. 
>- However, it is common usage to refer to say "$E$" when we really mean "$L(E)$".
>- We shall use this convention as long as it is clear we are talking about a language and not about a regular expression
>  
>-- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 89  

>[!important]
>The **regular expression** induces the *algebraic structure* $$(\mathcal{R}, \;|, \;\cdot, \;*)$$ or $$(\mathcal{R}, \;+, \;\cdot, \;*)$$ 

- 

>[!important]
>**Regular expressions** can often be created ("*induced*" or "*learned*") based on a set of *example strings*.
>- This is called the **induction of regular expression**


>[!info]
>Note that the **dot** $\cdot$ can optionally be used to denote the **concatenation operator**, either as an operation on *languages* or as the *operator in a regular expression*.
>- For instance, $$0 \cdot 1$$ means $$ 01 \text{ or language }\{ 01 \}$$
>- We should avoid using dot as **concatenation in regular expression**


- [[Regular Expression Pattern Basics]]
- [[Regular Expression Advanced Operations]]

>[!info]
>We should note the difference between $$\Sigma^{*} \quad \text{ and} \quad L^{*}$$
>- $\Sigma$ is the set of *symbols*
>- $L$ is the set of *strings* with $L \subset \Sigma^{*}$
>- But both $\Sigma^{*}$ and $L^{*}$ are the *same language*   $$L^{*} = \Sigma^{*}$$

- [[Language Generated by Grammar]]

## Finite Automata and Regular Expression

- [[Regular Expression and Finite Automata Equivalence]]


-----------
##  Recommended Notes and References



- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp 85 - 166
- [[Speech and Language Processing by Jurafsky]] pp 5, 29 - 30
- [[Foundations of Machine Learning by Mohri]] pp 361
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 120
- [[Artificial Intelligence Modern Approach by Russell]] pp 874