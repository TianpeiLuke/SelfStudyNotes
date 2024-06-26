---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/measure_theory
keywords:
  - uniform_convergence
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: uniform convergence
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Uniform Convergence


>[!important] Definition
>We say that $f_n$ *converges* to $f$ **uniformly** if,  for any $\epsilon > 0$, there exists $N > 0$ (that *depends on $\epsilon$ only*)  such that for all $n \ge N$, $$| f_n(x) - f(x) | \leq  \epsilon$$  for *every* $x \in X$. Denoted as $f_{n} \rightarrow f, \text{uniformly}$.


>[!important] Alternative Definition (General Metric Space)
>We say that $f_n$ *converges* to $f$ **uniformly** if,  for any $\epsilon > 0$, there exists $N > 0$  such that for all $n \ge N$, 
>$$
>\sup\{ \bar{d}(f_{n}(x), f(x)): x\in X \} \le \epsilon,
>$$
>where $\bar{d}$ is the bounded metric induced by metric $d$.

- [[Uniform Topology on Metric Spaces]]


## Explanation

>[!important]
>**Uniform convergence** is the convergence with respect to **uniform topology**.

- [[Uniform Topology on Metric Spaces]]

>[!important]
>*Uniform convergence* is also called **convergence in $L^{\infty}$ norm**.

- [[Lp Space]]



-----------
##  Recommended Notes and References

- [[Pointwise Convergence]]
- [[Uniformly Almost Everywhere Convergence]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)