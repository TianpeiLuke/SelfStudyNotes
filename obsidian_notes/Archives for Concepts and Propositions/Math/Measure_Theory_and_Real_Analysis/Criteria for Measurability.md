---
tags:
  - concept
  - math/measure_theory
keywords:
  - criteria_measurability
topics:
  - measure_theory
name: Criteria for Measurability
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Criteria for Measurability


>[!important] Proposition
>The followings are equivalent:
> 
> 1. $E$ is **Lebesgue measureable.**
> 2. **Outer approximation** by *open*: For every $\epsilon>0$, one can contain $E$ in an *open* set $U$ with $$m^{*}(U \setminus  E)\le \epsilon .$$
> 3. **Almost open**: For every $\epsilon>0$, one can find an *open* set $U$ such that  $$m^{*}(U\Delta E)\le \epsilon,$$where $U\Delta E = (U  \setminus  E)\cup (E  \setminus  U) = (U\cup E) \setminus  (U\cap E)$ is the **symmetric difference.** (In other words, $E$ differs from an open set by a set of outer measure *at most* $\epsilon$.)
> 4. **Inner approximation** by *closed* For every $\epsilon>0$, one can find a *closed* set $F$ contained in $E$ with $$m^{*}(E  \setminus  F)\le \epsilon.$$
> 5. **Almost closed**: For every $\epsilon>0$, one can find a *closed* set $F$ such that $$m^{*}(E\Delta F)\le \epsilon.$$ (In other words, $E$ differs from a closed set by a set of outer measure *at most* $\epsilon$.)
> 6. **Almost measurable**: For every $\epsilon>0$, one can find a Lebesgue measurable set $E_{\epsilon}$ such that $$m^{*}(E\Delta E_{\epsilon})\le \epsilon.$$ (In other words, E differs from a measurable set $E_{\epsilon}$ by a set of outer measure *at most* $\epsilon.$)




## Explanation






-----------
##  Recommended Notes and References

- [[Lebesgue Measure]]
- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis by Royden]]