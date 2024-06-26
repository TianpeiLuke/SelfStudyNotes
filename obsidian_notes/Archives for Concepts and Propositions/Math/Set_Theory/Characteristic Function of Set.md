---
tags:
  - concept
  - math/set_theory
  - math/functional_analysis
  - math/real_analysis
  - math/probability
keywords:
  - characteristic_function_set
topics:
  - set_theory
  - functional_analysis
  - real_analysis
name: Characteristic Function of Set
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Characteristic Function of Set

>[!important] Definition
>Let $A \subset \mathcal{X}$ be a subset.
>
>The **characteristic function** of $A$ is defined as $\chi_{A}: \mathcal{X} \to \{ 0, 1 \}$ 
>$$
> \chi_{A}(x) := \left\{
> \begin{array}{cc}
> 1 & x \in A \\ 
> 0 & x \not\in A
>\end{array}
> \right.
>$$
>
>The characteristic function is also called the **indicator function**, and denoted as $$\mathbb{1}_{A}(x).$$

### Relation

>[!important] Definition
>Let $R \subset \mathcal{X} \times \mathcal{Y}$ be a relation.
>
>The **characteristic function** of $R$ is defined as $\chi_{R}: \mathcal{X} \times \mathcal{Y}\to \{ 0, 1 \}$ 
>$$
> \chi_{R}(x, y) := \left\{
> \begin{array}{cc}
> 1 & (x, y) \in R \\ 
> 0 & (x, y) \not\in R
>\end{array}
> \right.
>$$
>
>It can be denoted as $$\chi_{R}(x, y)  := \left[ (x,y) \in R \right] $$

- [[Relation]]

>[!important] Definition
>Let $R \subset \mathcal{X}_{1} \,{\times}\ldots{\times}\, \mathcal{X}_{n}$ be a relation.
>
>The **characteristic function** of $R$ is defined as $\chi_{R}: \mathcal{X}_{1} \,{\times}\ldots{\times}\, \mathcal{X}_{n} \to \{ 0, 1 \}$ 
>$$
> \chi_{R}(x_{1} \,{,}\ldots{,}\, x_{n}) := \left\{
> \begin{array}{cc}
> 1 & (x_{1} \,{,}\ldots{,}\, x_{n}) \in R \\ 
> 0 & (x_{1} \,{,}\ldots{,}\, x_{n}) \not\in R
>\end{array}
> \right.
>$$
>
>It can be denoted as $$\chi_{R}(x_{1} \,{,}\ldots{,}\, x_{n})  := \left[ (x_{1} \,{,}\ldots{,}\, x_{n}) \in R \right] $$


## Explanation


## Set Operations

>[!important] Proposition
>For any $A, B \subset \mathcal{X}$, 
>- **Inclusion**: if $A \subset B$, then $$\chi_{A} \le \chi_{B}$$
>- **Intersection**: $$\chi_{A \cap B} = \chi_{A}\;\chi_{B}$$
>- **Union**: $$\chi_{A \cup B} = \chi_{A} + \chi_{B}$$
>- **Complement**: $$\chi_{\mathcal{X} \,\setminus\, A} = 1 - \chi_{A}$$
>- **Difference**: $$\chi_{ B\,\setminus\, A} = \chi_{B}(1 - \chi_{A})$$
>- **Symmetric Difference**: $$\chi_{ B\,\Delta\, A} = \chi_{B}(1 - \chi_{A}) + \chi_{A}(1 - \chi_{B}).$$

- [[Set Operations]]

## Limits of Set

- [[Limits of Sets]]



## Simple Function







-----------
##  Recommended Notes and References


- [[Atomic Algebra]]
- [[Simple Integral of Simple Functions]]

- [[Evaluation Functional]]
- [[Delta Function]]

- [[Function]]
- [[Set Operations]]

- Wikipedia [Characteristic_function](https://en.wikipedia.org/wiki/Characteristic_function)
- Math Wikipedia [Characteristic_Function_](https://proofwiki.org/wiki/Definition:Characteristic_Function_(Set_Theory))