---
tags:
  - concept
  - math/set_theory
keywords:
  - supremum_set
  - infimum_set
topics:
  - set_theory
name: Supremum and Infimum of  Sets
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Supremum and Infimum of Sets


>[!important] Definition
>The **infimum** and the **supremum** of a collection of sets $\{E_{n}\}_{n\ge k}$ is given by 
>$$
> \begin{align*}
> &\inf\limits_{n\ge k}E_{n} = \bigcap_{n= k}^{\infty}E_{n}, \quad \sup\limits_{n\ge k}E_{n} = \bigcup_{n= k}^{\infty}E_{n} ,
> \end{align*}
>$$ 
>respectively.

- [[Upper Bound and Supremum of Set]]
- [[Lower Bound and Infimum of Set]]

## Explanation

>[!important]
>For any $n \ge k$,
>$$
>\inf_{i\ge k}E_{i} \subseteq E_{n} \subseteq \sup_{i\ge k}E_{i}.
>$$
>Thus the infimum and supremum of sets defines the lower bound and upper bound of the sets in the given collection.

>[!info]
>In probability, both infimum and supremum of sets describe a collection of **the tail events**  $$\{E_{n}\}_{n\ge k},$$ a sequence of events that are *statistical independent* from a *finite* $k$ collection of events.

## Examples

>[!example]
>Let $\{f_{n}\}$ and $f$ be real-valued measurable functions on $X$. 
>
>Define an event as 
>$$E_{n,\epsilon} := \set{x \in X: | f_n(x) - f(x) | \ge \epsilon}.$$ 
>Then the **supremum** and the **infimum** of event are
>$$
>\sup_{n \ge k}E_{n, \epsilon} := \bigcup_{n\ge k}E_{n,\epsilon} = \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad \exists n \ge k \right\}
>$$
>and
>$$
>\inf_{n \ge k}E_{n, \epsilon} := \bigcap_{n\ge k}E_{n,\epsilon} = \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad \forall n \ge k \right\}
>$$

- [[Tail Support and Width]]


## Nested Sequence of Supremums and Infimums

>[!important]
>Note that a collection of infimums of sets forms a *nested sequence* of sets that is **monotone increasing**: 
>$$
>\inf\limits_{n\ge k}E_{n} = \bigcap_{n= k}^{\infty}E_{n} \supseteq \bigcap_{n= k+1}^{\infty}E_{n} = \inf\limits_{n\ge k+1}E_{n}.
>$$
>Also, a collection of supremums of sets forms a *nested sequence* of sets that is **monotone decreasing**: 
>$$
>\sup\limits_{n\ge k}E_{n} = \bigcup_{n= k}^{\infty}E_{n} \subseteq \bigcup_{n= k+1}^{\infty}E_{n} = \sup\limits_{n\ge k+1}E_{n}.
>$$

This is because

>[!example]
>Note that given any *countable* collection of sets $E_{i}$, $i=1 \,{,}\ldots{,}\,$,  for any finite $n\in \mathbb{N}$,
>$$
>\bigcup_{i=k}^{n}E_{i} \supseteq \bigcup_{i=k+1}^{n}E_{i}
>$$
>and
>$$
>\bigcap_{i=k}^{n}E_{i} \subseteq \bigcap_{i=k+1}^{n}E_{i}.
>$$
>
>In other word, 
>- $\{ \bigcap_{i=k}^{n}E_{i} \}_{k}$ is a **nested** sequence of **monotone increasing** sets.
>- $\{ \bigcup_{i=k}^{n}E_{i} \}_{k}$ is a **nested** sequence of **monotone decreasing** sets.






-----------
##  Recommended Notes and References

- [[Set Operations]]
- [[Monotone Sequence of Nested Sets]]