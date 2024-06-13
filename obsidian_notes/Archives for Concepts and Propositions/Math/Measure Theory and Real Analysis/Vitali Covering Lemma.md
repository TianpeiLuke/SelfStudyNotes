---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - vitali_covering_lemma
topics:
  - real_analysis
name: Vitali Covering Lemma
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Vitali Covering Lemma

>[!important] Vitali Covering Lemma
>Suppose $E$ is a set of *finite measure* and $\mathcal{B}$ is a **Vitali covering** of $E$. 
>
>For any $\delta>0$, we can find **finitely many balls** $B_{1},\ldots, B_{N}$ in $\mathcal{B}$ that are **disjoint** and so that 
>$$
> \begin{align*}
> \sum_{i=1}^{N}m(B_{i}) &\ge m(E) - \delta
> \end{align*}
>$$ 

- [[Vitali Covering]]
- [[Covering of Set and Open Covering of Topological Set]]

>[!important] Corollary
>Following the setting above, we can arrange the choice of balls so that
>$$
> \begin{align*}
> m\left( E- \bigcup_{i=1}^{N}B_{i} \right) &< 2\delta
> \end{align*}
>$$ 



## Explanation





-----------
##  Recommended Notes and References

- [[Vitali Covering]]
- [[Covering of Set and Open Covering of Topological Set]]



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]