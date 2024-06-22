---
tags:
  - concept
  - math/measure_theory
  - math/functional_analysis
keywords:
  - outer_regularity
topics:
  - measure_theory
  - functional_analysis
name: outer regularity
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Outer Regularity


>[!important] Defintion
>Let $\mu$ be a *Borel measure* on $X$ and $E$ a *Borel subset* of $X$. The measure $\mu$ is called **outer regular** on $E$  if
>$$
>\begin{align*}
>\mu(E) &= \inf\set{\mu(U): U \supseteq E, U \text{ is open}}
>\end{align*}
>$$

## Explanation

>[!info]
>**Outer regular** involves *an open set* **covering** the Borel set being measured. Thus the Borel set of interest is *approximated* by an "outer" set.
>
>For outer regularity holds, the *measure* of an Borel set of interest can be *approximated* by the **lower bound** of the *measure* of *any open superset*



>[!info]
>Note that due to the inclusion of **topology** of $\mathcal{X}$ in Borel $\sigma$-algebra, we are allowed to used *topological concepts* such as *open sets* in the definition of outer regularity.





-----------
##  Recommended Notes and References

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Inner Regularity]]

- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]