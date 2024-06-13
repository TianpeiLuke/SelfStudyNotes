---
tags:
  - concept
  - math/real_analysis
keywords:
  - riemann_integration
  - darboux_lower_sum
  - darboux_upper_sum
topics:
  - real_analysis
name: Darboux Lower Sum and Darboux Upper Sum
date of note: 2024-06-06
---

## Concept Definition

>[!important]
>**Name**: Darboux Lower Sum and Darboux Upper Sum

>[!important] Definition
>A **partition** $P$ *of* $[a, b]$ is a *finite set* of points from $[a, b]$ that includes both $a$ and $b$, i.e. $P = \left\{ x_{0}, x_{1} \,{,}\ldots{,}\, x_{n} \right\}$ in *increasing order*; thus
>$$a = x_{0} < x_{1} \,{<}\ldots{<}\, x_{n} = b.$$

>[!important] Definition
>Let $f: [a,b] \to \mathbb{R}$ be a *bounded function*, i.e. there exists some $M >0$ such that $$|f(x)| \le M$$ for all $x\in [a, b].$
>
>Given a partition $P = \left\{ x_{0}, x_{1} \,{,}\ldots{,}\, x_{n} \right\}$ of $[a,b]$, the **Darboux lower sum** of $f$ *with respect to* $P$ is defined as
>$$
>\begin{align*}
>L(f, P) := \sum_{k=1}^{n}m_{k}\left( x_{k} - x_{k-1} \right)
>\end{align*}
>$$
>where 
>$$
>m_{k} = \inf\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$
>
>Similarly, the **Darboux upper sum** of $f$ *with respect to* $P$  is defined as
>$$
>\begin{align*}
>U(f, P) := \sum_{k=1}^{n}M_{k}\left( x_{k} - x_{k-1} \right)
>\end{align*}
>$$
>where
>$$
>M_{k} = \sup\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$

>[!info]
>By definition, for fixed $P$, $$L(f, P) \le U(f, P).$$

### Refinement

>[!important] Definition
>A *partition* $Q$ is a **refinement** of a *partition* of $P$ if $Q$ contains all points of $P$; that is $$P \subseteq Q.$$

>[!important] Lemma
>If $P \subseteq Q$, then $$L(f, P) \le L(f, Q)$$ and $$U(f, P) \ge U(f, Q).$$

>[!important] Lemma
>If $P_{1}$ and $P_{2}$ are any two partitions of $[a,b]$, then $$L(f, P_{1}) \le U(f, P_{2}).$$

## Explanation

>[!info]
>The **Riemann lower integral** of $f$ is defined as
>$$
>\begin{align*}
>L(f) := \sup\left\{L(f, P): P\in \mathcal{P}  \right\}
>\end{align*}
>$$
>where $L(f, P)$ is the *Darboux lower sum* with respect to a partition $P\in \mathcal{P}$.
>
>Similarly, the **Riemann upper integral** of $f$ is defined as
>$$
>\begin{align*}
>U(f) = \sup\left\{ U(f, P): P\in \mathcal{P} \right\}
>\end{align*}
>$$
>where $U(f, P)$ is the *Darboux upper sum* with respect to a partition $P\in \mathcal{P}$.

- [[Riemann Integration]]




-----------
##  Recommended Notes and References



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]

- Rudin, W. (1964). _Principles of mathematical analysis_ (Vol. 3). New York: McGraw-hill.
- Abbott, S. (2015). _Understanding analysis_. Springer.