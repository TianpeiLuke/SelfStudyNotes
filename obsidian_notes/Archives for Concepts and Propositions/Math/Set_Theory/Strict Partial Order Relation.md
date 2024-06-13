---
tags:
  - concept
  - math/set_theory
keywords:
  - strict_partial_order_relation
topics:
  - set_theory
name: Strict Partial Order Relation
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Strict Partial Order Relation

>[!important] Definition
>Given a set $A$, a relation $\prec$ on $A$ is called a **strict partial order** on $A$ if it has the following two properties:
>
> - **Nonreflexivity**: The relation $a \prec a$ never holds.
> - **Transitivity** If $a \prec b$ and $b \prec c$, then $a \prec c$.
> 
> Moreover, suppose that we define $a \preceq b$ either $a \prec b$ or $a = b$. Then the relation $\preceq$ is called a **partial order** on $A$.


## Explanation

>[!info]
>Compare to order relation [[Simple Order Relation]], the **strict order relation** *do not have* the followoing property:
> - **Comparability**: For every $x$ and $y$ in $A$ for which $x \neq y$, **either $xCy$ or $yCx$**.
>
>In other word, not every pair of elements in $A$ can compare under $\prec$ relation.
  
>[!info]
>In term of graph, *the strict order relation graph* is **not a complete graph**, i.e. not every pair of nodes are directly connected in the graph. The rest properties hold the same for order relation graph.



-----------
##  Recommended Notes and References

- [[Simple Order Relation]]
- [[Topology Book by Munkres]]