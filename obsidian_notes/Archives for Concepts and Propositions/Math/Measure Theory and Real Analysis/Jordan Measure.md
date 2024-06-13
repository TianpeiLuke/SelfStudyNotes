---
tags:
  - concept
  - math/measure_theory
keywords:
  - jordan_measure
topics:
  - measure_theory
name: Jordan measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Jordan Measure $m$


>[!info]
>A generalized measure of set $E$ can be induced by *elementary measure* of subset that **inscribed** $F$ or **circumscribed** $G$ of it: $F\subseteq E \subseteq G$. 

- **outer Jordan measure**
>[!important] Definition
>The **outer Jordan measure** is defined as 
>
>$$
>\begin{align*}
>m^{*, J}(E) &= \inf\limits_{G\in \mathscr{A}, G\supseteq E}m(G)
>\end{align*}
$$

- **inner Jordan measure**
>[!important] Definition
>The **inner Jordan measure** is defined as 
>
>$$
>\begin{align*}
>m_{*, J}(E) &= \sup\limits_{F\in \mathscr{A}_{0}, F\subseteq E}m(F)
>\end{align*}
>$$

- **Jordan measure**
>[!important] Definition
>If $$m^{*, J}(E)  = m_{*, J}(E),$$ then $E$ is **Jordan measureable** and denote $$m(E) \equiv m^{*, J}(E)  = m_{*, J}(E). $$


## Explanation






-----------
##  Recommended Notes and References

- [[Elementary Measure]]