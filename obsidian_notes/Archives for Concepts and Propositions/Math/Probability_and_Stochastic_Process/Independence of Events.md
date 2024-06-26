---
tags:
  - concept
  - math/probability
keywords:
  - independence_probabililty
topics:
  - probability
name: Independence of Events
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Independence of Events


>[!important] Definition
>Suppose  $(\Omega, \mathscr{F}, \mathcal{P})$ is a fixed *probability space.* *Events* $A$, $B \in \mathscr{F}$ are **independent** if
>$$
> \begin{align*}
> \mathcal{P}(A \cap B) = \mathcal{P}(A) \, \mathcal{P}(B).
> \end{align*}
>$$


>[!important] Definition
>The events $A_1 \,{,}\ldots{,}\, A_n$ are **independent** if
>$$
>\begin{align*}
>\mathcal{P}\left( \bigcap_{i = 1}^{n} B_i \right) &= \prod_{i =1}^{n}\mathcal{P}(B_i)
>\end{align*}
>$$
>where
>$$
> \begin{align*}
> B_i = A\text{ or }\Omega, \quad i = 1 \,{,}\ldots{,}\, n.
> \end{align*}
>$$

>[!important] Definition
>Let $$\mathscr{B}_i \subseteq \mathscr{F},$$ for $i = 1  \,{,}\ldots{,}\, n.$ 
>
>The classes $\mathscr{B}_i$ are  **independent**, if for *any choice* $A_1 \,{,}\ldots{,}\, A_n$, with $A_i \in \mathscr{B}_i$, $i = 1 \,{,}\ldots{,}\, n$, we have the events $A_1 \,{,}\ldots{,}\, A_n$ **independent events**.


## Explanation





-----------
##  Recommended Notes and References

- [[Probability Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)