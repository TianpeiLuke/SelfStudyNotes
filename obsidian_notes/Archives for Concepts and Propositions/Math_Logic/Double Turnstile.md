---
tags:
  - concept
  - logic/math_logic
keywords:
  - double_turnstile
topics:
  - math_logic
name: Double Turnstile
date of note: 2024-07-17
---

## Concept Definition

>[!important]
>**Name**: Double Turnstile

>[!important] Definition
>In **logic**, the symbol $\vDash$ or $\models$ is called the **double turnstile**. 
>
>It is often read as "*entails*", "*models*", "is a *semantic consequence* of", "is *stronger* than".

## Explanation


>[!important]
>The *double turnstile* is a **binary relation**. It has several different meanings in different contexts:
>- To show **semantic consequence**, with a *set of sentences* on the left and a *single sentence* on the right, to denote that if *every* sentence on the left is *true*, the sentence on the right *must be tru*e, e.g. $\Gamma \vDash \phi$. 
>	- This usage is closely related to the *single-barred turnstile* symbol which denotes **syntactic consequence**.
> - To show **satisfaction**, with a **model** (or truth-structure) on the *left* and a *set of sentences* on the right, to denote that the *structure* is a model for (or *satisfies*) the set of *sentences*, e.g. $\mathcal{A} \vDash \Gamma$. 
> 	- This is typically done **inductively** along with restricting the range of a _variable assignment_, a function mapping each variable symbol to a value in $\mathcal{A}$ it might hold.
> 	- In this context, the semantic consequence in the previous list can be stated as "For a given model $\mathcal{A}$, if $\mathcal{A} \vDash \Gamma$ then $\mathcal{A} \vDash \phi$".
> - To denote a **tautology**, $\vDash \phi$. which is to say that the expression $\phi$ is a semantic consequence of the empty set.
> - You can also use this symbol as follows: $\nvDash$ to denote the statement '*does not entail*'.





-----------
##  Recommended Notes and References


- Wikipedia [Double_turnstile](https://en.wikipedia.org/wiki/Double_turnstile)
- Wikipedia [List_of_logic_symbols](https://en.wikipedia.org/wiki/List_of_logic_symbols)
- Wikipedia [List_of_LaTeX_mathematical_symbols](https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols)