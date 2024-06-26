---
tags:
  - concept
  - math/measure_theory
keywords:
  - dominated_convergence_theorem
topics:
  - measure_theory
name: Dominated Convergence Theorem
date of note: 2024-05-07
---

## Theorem

>[!important]
>**Name**:  Dominated Convergence Theorem


>[!important] Theorem
>Let $(X, \mathscr{B}, \mu)$ be a measure space, and let $f_1 \,{,}\ldots{,}\,  f_n: X  \rightarrow \mathbb{C}$ be a sequence of measurable functions that converge  **pointwise $\mu$-almost everywhere** to a *measurable limit* $f : X\rightarrow \mathbb{C}$, i.e.
>$$
>\begin{align*}
>f_{n} \stackrel{\text{a.e.}}{\rightarrow }f.
>\end{align*}
>$$
>
>Suppose that there is an **unsigned absolutely integrable** function $G : X\rightarrow [0, +\infty]$ such that $\left\lvert f_{n} \right\rvert$ are *pointwise $\mu$-almost everywhere* **bounded** by $G$ for each $n$. 
>$$
>\begin{align*}
>\left\lvert f_{n} \right\rvert \le G,\; \text{a.e.}
>\end{align*}
>$$
>Then we have
> $$
> \begin{align*}
> \lim\limits_{n\rightarrow \infty}\int_{X}f_{n} d\mu &= \int_{X} \left( \lim\limits_{n\rightarrow \infty} f_{n} \right) d\mu = \int_{X} f d\mu
> \end{align*}
> $$

- [[Absolutely Convergent Integration]]

- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Monotone Convergence Theorem]]


## Explanation






-----------
##  Recommended Notes and References

- [[Fatou Lemma]]

- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Probability and Measure by Billingsley]]