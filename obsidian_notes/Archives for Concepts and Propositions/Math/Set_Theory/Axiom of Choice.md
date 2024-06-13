---
tags:
  - concept
  - math/set_theory
keywords:
  - axiom_choice
topics:
  - set_theory
name: Axiom of Choice
date of note: 2024-05-10
---

## Theorem

>[!important]
>**Name**: Axiom of Choice

>[!important] Axiom of Choice
>Given a collection $\mathscr{A}$ of **disjoint** *nonempty sets*, there **exists** *a set* $C$ consisting of **exactly one element from each element of $\mathscr{A}$**; 
>
>that is, a set $C$ such that $C$ is contained in the **union of the elements** of $\mathcal{A}$, and for each $A \in \mathscr{A}$, the set $C \cap A$ contains **a single element**.


>[!info]
>$$
>C \subset \bigcup_{A\in \mathscr{A}}A, \quad C\cap A = \{x_{A}\}
>$$

## Explanation

>[!info]
>Formally, it can be expressed as below:
>$$
>\begin{align*}
>(\forall \mathscr{A})\left[ \emptyset\not\in \mathscr{A} \implies \quad \exists f: \mathscr{A} \to \bigcup_{A \in \mathscr{A}}A: \; (\forall A \in \mathscr{A})\,f(A) \in A  \right]
\end{align*}
>$$

## Equivalent Theorems

>[!important]
>The following three fundamental theorems are equivalent:
>- **Well-Ordering Theorem**: [[Well Ordering Theorem]] 
>- **The Axiom of Choice**: [[Axiom of Choice]]
>- **Zorn's Lemma**: [[Zorn Lemma]]



-----------
##  Recommended Notes and References


- [[Topology Book by Munkres]]