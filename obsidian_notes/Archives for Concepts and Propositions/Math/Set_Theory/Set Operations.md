---
tags:
  - concept
  - math/set_theory
keywords:
  - set_operations
topics:
  - set_theory
name: Set Operations
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Set Operations

>[!important] Definition
>Given a set $X$, **the collection of all subsets** of $X$, denoted as $2^X$, is defined as
>$$
> \begin{align*}
> 2^X &:= \{E: E \subseteq X \}
> \end{align*}
>$$ 

>[!important] Basic Set Operations
The followings are basic operation on $2^X$: For $A, B \in 2^X$,
> 
> - **Inclusion**:   $A \subseteq B$ if and only if $\forall x \in A$, $x \in B$.
> - **Union**:  $A \cup B = \set{x: x \in A \lor x \in B}$.
> - **Intersection**:  $A \cap B = \set{x: x \in A \land x \in B}$.
> - **Difference**:  $A \setminus B = \set{x: x \in A \land x \not\in B}$.
> - **Complement**: $A^{c} = X \setminus A = \set{x: x \in X \land x \not\in A}$.
> - **Symmetric Difference**:  $A \Delta B = (A \setminus B) \cup (B \setminus A) = \set{x \in X: x \not\in A \lor x \not\in B}$.
> 
> - **deMorgan's Laws**:
>$$
> \begin{align*}
> \left(\bigcup_{a \in A}U_a\right)^c &= \bigcap_{a \in A}U_a^c \\
> \left(\bigcap_{a \in A}U_a\right)^c &= \bigcup_{a \in A}U_a^c
> \end{align*}
>$$ 


## Explanation





-----------
##  Recommended Notes and References

