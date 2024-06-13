---
tags:
  - concept
  - math/set_theory
  - math/topology
keywords:
  - cartestian_product
topics:
  - set_theory
  - topology
name: Arbitrary Cartestian Products
date of note: 2024-05-13
---

## Concept Definition

>[!important]
>**Name**: Arbitrary Cartestian Products

>[!important] Definition
>Let $\{A_{\alpha}\}_{\alpha \in J}$ be an *indexed family* of sets; let $$X = \bigcup_{\alpha \in J}A_{\alpha}.$$ 
>
>The **cartesian product** *of this indexed family*, denoted by
>$$
> \begin{align*}
> \prod_{\alpha \in J} A_{\alpha}
> \end{align*}
>$$ 
> is defined to be *the set of all $J$-tuples* $(x_{\alpha})_{\alpha \in J}$ of elements of $X$ such that $$x_{\alpha} \in A_{\alpha}$$ for each $\alpha \in J$. 
> 
> That is, it is *the set of all functions*
>$$ 
> \begin{align*}
> x: J \rightarrow \bigcup_{\alpha \in J}A_{\alpha}
> \end{align*}
>$$ 
> such that $x(\alpha) \in A_{\alpha}$ for each $\alpha \in J$.

- [[Indexed Family of Sets]]
 - [[J Tuples]]

>[!important] Definition
> Now let $\{A_1, A_2, \ldots \}$  be a family of sets, **indexed with the positive integers**; let $X$ be the *union* of the sets in this family. 
> 
>The **cartesian product** of this *indexed family of sets*, denoted by
>$$
> \begin{align*}
> \prod_{i \in \mathbb{N}} A_i \quad \text{ or } \quad A_1 \times A_2 \times \ldots , 
> \end{align*}
>$$ 
> is defined to be **the set of all $\omega$-tuples** $(x_1, x_2, \ldots )$ of elements of $X$ such that $$x_i \in A_i$$ for each $i$.

- [[omega Tuples]]

## Explanation

>[!important]
>The *existance* of just construction is due to **the Axioms of Choice** since $J$ is an *arbitrary set*.

- [[Axiom of Choice]]




-----------
##  Recommended Notes and References

- [[J Tuples]]

- [[Zorn Lemma]]

- [[Topology Book by Munkres]]