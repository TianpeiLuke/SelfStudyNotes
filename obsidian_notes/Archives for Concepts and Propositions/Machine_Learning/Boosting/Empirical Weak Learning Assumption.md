---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - Probably_Approximately_Correct
  - weak_probabily_approximately_correct
  - weak_learnable
topics:
  - machine_learning_theory
name: Empirical Weak Learning Assumption
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Empirical Weak Learning Assumption

![[Empirical Risk Minimization#^a84128]]

![[Empirical Risk Minimization#^c9ebc0]]

![[Weak PAC Learnablity#^6b4c5c]]


>[!important] Definition
>The **empirical $\gamma$-weak learning assumption** states that there exists $h^{*} \in \mathcal{H}$ such that the *training error*
>$$
>L_{\mathcal{D}}(h^{*}) = \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h^{*}(X_{i}) \neq l(X_{i})\} \le \frac{1}{2} - \gamma.
>$$
>We also say the hypothesis class $\mathcal{H}$ satisfies the **weak learning assumption.**

- [[Weak PAC Learnablity]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Realizability Assumption for Empirical Risk Minimization]]


## Explanation



-----------
##  Recommended Notes and References

- [[Weak PAC Learnablity]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]
- [[Rademacher Complexity]]
- [[VC Dimension]]

- [[Cramér–Chernoff Method]]


- [[Boosting Foundations and Algorithms by Schapire]]  pp 46