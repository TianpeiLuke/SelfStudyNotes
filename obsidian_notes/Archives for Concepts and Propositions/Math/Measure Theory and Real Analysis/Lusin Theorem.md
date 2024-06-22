---
tags:
  - concept
  - math/real_analysis
keywords:
  - lusin_theorem
topics:
  - real_analysis
name: Lusin Theorem
date of note: 2024-05-28
---

## Theorem

>[!important]
>**Name**: Lusin's Theorem

>[!important] Lusin's Theorem
>Let $f : \mathbb{R}^d \rightarrow \mathbb{C}$ be **absolutely integrable**, and let $\epsilon > 0$. 
>
>Then there exists a *Lebesgue measurable set* $E \subset \mathbb{R}^d$ of measure **at most $\epsilon$** such that the **restriction** of $f$ to the **complementary set** $\mathbb{R}^d \setminus E$ is **continuous** on that set. 


- [[Continuous Function]]
- [[Absolutely Convergent Integration]]

## Proof

>[!info]
>By $L^{1}$ approximations, for any $n \ge 1$ one can find a **continuous, compactly supported** function $f_n \in \mathcal{C}_{0}(\mathbb{R})$ such that $$\lVert f -f_n \rVert_{L^1(\mathbb{R}^d)} \le \epsilon/4^{n}.$$ 
>
>By **Markov's inequality**, that implies that $$\left\lvert f(x) -f_n(x) \right\rvert\le 1/2^{n-1}$$  for all $x$ *outside* of a Lebesgue measurable set $A_n$ of measure *at most $\epsilon/2^{n+1}$*. 

- [[Simple Approximation Theorem of Lp Function]]
- [[Markov Inequality]]
- 

>[!info]
>Letting $$A = \bigcup_{n=1}^{\infty}A_{n},$$ we conclude that $A$ is *Lebesgue measurable* with measure *at most $\epsilon/2$*, and $f_n$ converges *uniformly* to $f$ outside of $A$. 
>

>[!info]
>But the **uniform limit of continuous functions is continuous**, and the same is true for *local uniform limits* (because continuity is itself a local property). 
>
>We conclude that the restriction $f$ to $\mathbb{R}^{d} \setminus  E$ is continuous, as required. QED

- [[Uniform Continuity Theorem]]


## Explanation

>[!important]
>This theorem **does not imply** that the **unrestricted function** $f$ is **continuous** on $\mathbb{R}^d \setminus  E$. 
>
>For instance, the absolutely integrable function $\mathbb{1}(\mathbb{Q}) : \mathbb{R} \rightarrow \mathbb{C}$ is *nowhere continuous*, so is certainly *not continuous* on $\mathbb{R} \setminus  E$ for any $E$ of *finite measure*; 
>
>but on the other hand, if one *deletes the measure zero set* $E \equiv \mathbb{Q}$ from the reals, then the restriction of $f$ to $\mathbb{R} \setminus  E$ is *identically zero* and thus continuous. [[Introduction to Measure Theory by Tao]]


>[!important] 
>When dealing with **unsigned measurable functions** such as $f : \mathbb{R}^d \rightarrow [0,+\infty]$, then *Lusin's theorem* **does not apply directly** because $f$ could be **infinite on a set of positive measure**, which is clearly in contradiction with the conclusion of Lusin's theorem (unless one allows the continuous function to also take values in the extended non-negative reals $[0,+\infty]$ with the extended topology). 
>
>However, if one knows already that **$f$ is almost everywhere finite** (which is for instance the case when $f$ is *absolutely integrable* ), then **Lusin's theorem applies** (since one can simply *zero out* $f$ on the *null set where it is infinite*, and add that null set to the exceptional set of Lusin's theorem).





-----------
##  Recommended Notes and References

- [[Absolutely Convergent Integration]]
- [[Continuous Function]]
- [[Measurable Function]]
