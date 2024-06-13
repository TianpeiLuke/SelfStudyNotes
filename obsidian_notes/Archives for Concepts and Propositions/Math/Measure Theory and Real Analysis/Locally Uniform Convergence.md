---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - locally_uniform_convergence
topics:
  - measure_theory
  - real_analysis
name: Locally Uniform Convergence
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Locally Uniform Convergence

>[!important] Definition
>A sequence of functions $f_n : \mathbb{R}^d \rightarrow \mathbb{C}$ *converges* **locally uniformly** to a limit $f : \mathbb{R}^d \rightarrow \mathbb{C}$ if, for every *bounded* subset $E$ of $\mathbb{R}^d$, $f_n$ converges *uniformly* to $f$ on $E$. 
>
>In other words, for *every bounded* $E \subset \mathbb{R}^d$ and any $\epsilon > 0$, there exists $N > 0$ such that for all $n \ge N$ and $x \in E$, 
>$$\lVert f_n(x) - f(x) \rVert  \le  \epsilon.$$ 

- [[Uniform Convergence]]

>[!important] Alternative Definition (General Metric Space)
>We say that $f_n$ *converges* to $f$ **locally uniformly** if,  for any $\epsilon > 0$, and for any *bounded subset* $E \subset X$, there exists $N > 0$  such that for all $n \ge N$, 
>$$
>\sup\{ \bar{d}(f_{n}(x), f(x)): x\in E \} \le \epsilon,
>$$
>where $\bar{d}$ is the bounded metric induced by metric $d$.


## Explanation

>[!important]
>In $\mathbb{R}^d$, the locally uniform convergence is equivalent to **convergence in compact topology** since *closed bounded set* in $\mathbb{R}^d$ is compact

- [[Topology of Compact Convergence]]






-----------
##  Recommended Notes and References

- [[Uniform Convergence]]
- [[Introduction to Measure Theory by Tao]]