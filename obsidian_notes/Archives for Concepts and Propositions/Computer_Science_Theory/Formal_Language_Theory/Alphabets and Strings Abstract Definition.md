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
  - alphabet_formal_language
  - strings_formal_language
topics:
  - computational_linguistic/language
  - computer_science/formal_language
name: Alphabets and Strings Abstract Definition
date of note: 2024-12-15
---

## Concept Definition

>[!important]
>**Name**: Alphabets and Strings Abstract Definition

### Alphabet

>[!important] Definition
>An **alphabet** $\Sigma$ is a *finite*, nonempty set of *symbols*.

^e5b7e8

- [[Formal Language Abstract Definition]]
- [[Regular Expression Definition]]

>[!example]
>**Binary alphabet** is defined as $$\Sigma = \{ 0, 1 \}$$

### String

>[!important] Definition
>A **string** or a **string** $w$ is a *finite sequence* of symbols chosen from some alphabet.
>- The number of **positions** of symbols in a string is defined as the **length** of the string. $$\text{len}(w) := |w|$$
>- The **empty string** is the string with zero length $$\epsilon \implies |\epsilon| = 0$$ An empty string can be chosen from *any alphabet*.


### Power of Alphabet

>[!important] Definition
>Let $\Sigma$ be an *alphabet*. 
>
>The set of *all strings* of *given length* $d$ from that alphabet is called the **power of an alphabet** $$\Sigma^{d} := \{w: |w| = d \}$$  
>- The set of *all strings* from $\Sigma$ is denoted as $$\Sigma^{*} := \Sigma^{0} \cup \Sigma^{1} \cup \Sigma^{2} \cup \,{}\ldots{}\, = \Sigma^{+} \cup \{ \epsilon \}$$
>	- The star operator $*$ is called the **Kleene star**.
>- The set of *all nonempty string* from $\Sigma$ is denoted as $$\Sigma^{+} := \Sigma^{1} \cup \Sigma^{2} \cup \,{}\ldots{}$$

^339899


## Explanation


- [[Context-Free Grammars or CFG]]
- [[Context-Free Grammar Derivations]]
- [[Context-Free Language]]



-----------
##  Recommended Notes and References


- [[Introduction to Automata Theory Language and Computation by Hopcroft]] pp  28 - 30
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Speech and Language Processing by Jurafsky]]