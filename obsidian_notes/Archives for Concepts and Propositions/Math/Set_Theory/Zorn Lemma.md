---
tags:
  - concept
  - math/set_theory
keywords:
  - zorn_lemma
topics:
  - set_theory
name: Zorn's Lemma
date of note: 2024-05-10
---

## Theorem

>[!important]
>**Name**: Zorn's Lemma

>[!important] Theorem
>Let $A$ be a set that is **strictly partially ordered**. 
>
>If *every* **simply ordered** *subset* of $A$ has an **upper bound** in $A$, then $A$ has a **maximal element.**

- [[Strict Partial Order Relation]]
- [[Simple Order Relation]]
- [[Upper Bound and Supremum of Set]]
- [[Well Ordering Theorem]]


## Explanation

>[!info]
>Given an order relation $<$ on $A$ such that $<$ admits *nonreflexivity* and *transitivity* properties on $A$, then if for every $B\subset A$ such that  $<$ admits an additional *Comparability* property on $B$, the following holds  $$\sup B \in A,$$
>then $$\sup A \in A,$$
>holds as well.

>[!important]
>Zorn's Lemma can be seen as **an extension theorem**, which expands the domain of *supremum* from subsets to the whole set.

>[!important]
>Zorn's lemma identifies the **existence of supremum** in **extended set** using the *existence of supremum* within **each subset,** even if the latter's existence may not be inside each subset.  

>[!example]
>Note that the inclusion operation $\subset$  defines an order relationship between two sets. 
>
>One application of Zorn's lemma is on the collection of subsets $\mathscr{A} = \{A_{n}\}_{n \in J}$ that is partially ordered by $\subset$ operation. 
>
>For each simply ordered sub-collection of **nested sets**
>$$\mathscr{A}_{I}:=\{A_{n}\}_{n \in I},\quad I \subseteq J,$$ 
>where $A_i \subset A_{i+1}$ we can see that $A_{\max{I}}$ is the **upper bound** of $\mathscr{A}_{I}$ in $\mathscr{A}$. 
>
>Thus there exists a **maximal subset** $A_{max} \in \mathscr{A}$ so that $A_n \subset A_{max}$ for **all $n \in J$**.

>[!info]
>Zorn's Lemma is the typical use of **induction logic**, which *generalizes* the property from infinite number of nested subsets until eventually covering the whole set.

## How to Use Zorn's Lemma

>[!quote]
>If you are building a mathematical object in stages and find that (i) you have *not finished* even after *infinitely many stages*, and (ii) there seems to be *nothing to stop you continuing* to build, then Zorn’s lemma may well be able to help you.
> 
>—  [William Timothy Gowers](https://en.wikipedia.org/wiki/Timothy_Gowers "Timothy Gowers"), "How to use Zorn’s lemma"[^1]


## Example

>[!example]
>Use Zorn's Lemma to show that **every vector space $V$ has a basis.**

- [[Topological Vector Space]]

## Equivalent Theorems

>[!important]
>The following three fundamental theorems are equivalent:
>- **Well-Ordering Theorem**: [[Well Ordering Theorem]] 
>- **The Axiom of Choice**: [[Axiom of Choice]]
>- **Zorn's Lemma**: [[Zorn Lemma]]





-----------
##  Recommended Notes and References

- [[Simple Order Relation]]
- [[Topology Book by Munkres]]


[^1]: [William Timothy Gowers](https://en.wikipedia.org/wiki/Timothy_Gowers "Timothy Gowers") (12 August 2008). ["How to use Zorn's lemma"](https://gowers.wordpress.com/2008/08/12/how-to-use-zorns-lemma/).