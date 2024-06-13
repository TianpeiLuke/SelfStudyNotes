---
tags:
  - concept
  - math/measure_theory
  - math/functional_analysis
keywords:
  - inner_regularity
topics:
  - measure_theory
  - functional_analysis
name: inner regularity
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Inner Regularity


>[!important] Defintion
>Let $\mu$ be a *Borel measure* on $X$ and $E$ a *Borel subset* of $X$. The measure $\mu$ is called **inner regular** on $E$  if
>$$
> \begin{align*}
> \mu(E) &= \sup\set{\mu(C): C \subseteq E, C \text{ is compact}}
> \end{align*}
>$$ 

## Explanation

>[!info]
>**Inner regular** involves *a compact set* **contained inside** the Borel set being measured. Thus the Borel set of interest is *approximated* by the "inner" set.
>
>For inner regularity holds, the *measure* of the Borel set of interest can be *approximated* by the **upper bound** of the *measure* of *any compact subsets*





>[!info]
>Note that due to the inclusion of **topology** of $\mathcal{X}$ in Borel $\sigma$-algebra, we are allowed to used *topological concepts* such as *compactness* in the definition of inner regularity.





-----------
##  Recommended Notes and References

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Outer Regularity]]