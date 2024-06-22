---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - ascoli_theorem
topics:
  - functional_analysis
  - topology
name: Ascoli's Theorem
date of note: 2024-05-05
---

## Theorem

>[!important]
>**Name**:  Ascoli's Theorem


>[!important] Ascoli's Theorem
>Let $X$ be a **compact space**; let $(\mathbb{R}^n , d)$ denote *euclidean space* in either the square metric or the euclidean metric; give the space of *continuous functions* $\mathcal{C}(X, \mathbb{R}^n)$ the corresponding **uniform topology**. 
>
>A subspace $\mathscr{F}$ of $\mathcal{C}(X, \mathbb{R}^n)$ has **compact closure** *if and only if* $\mathscr{F}$ is **equicontinuous** and **pointwise bounded** under $d$.

- [[Compactness]]
- [[Metric Space]]
- [[Equicontinuity]]
- [[Pointwise Boundedness]]


### Corollary


>[!important] Corollary
>Let $X$ be **compact**; let $d$ denote either *the square metric* or *the euclidean metric* on $\mathbb{R}^n$; give $\mathcal{C}(X, \mathbb{R}^n)$ the corresponding **uniform topology**. 
>
>A subspace $\mathscr{F}$ of $\mathcal{C}(X, \mathbb{R}^n)$ is **compact** *if and only if* it is **closed**, **bounded** under the **sup metric** $\rho$, and **equicontinuous** under $d$.

- [[Compactness]]
- [[Sup Metric on Space of Bounded Functions]]
- [[Equicontinuity]]


>[!important] Corollary
>Let $X$ be **locally compact Hausdorff**; give $\mathcal{C}_0(X, \mathbb{R})$ the **uniform topology**. 
>
>A subset $\mathscr{F}$ of $\mathcal{C}_0(X, \mathbb{R})$ has **compact closure** *if and only if* it is **pointwise bounded**, **equicontinuous**, and **vanishes uniformly at infinity**.

- [[Locally Compact Hausdorff Space]]
- [[Continuous Functions that Vanish At Infinity]]
- [[Pointwise Boundedness]]
- [[Equicontinuity]]
- [[Compactness]]

## General Theorem

>[!important] Ascoli's Theorem, General Version
>
> Let $X$ be a space and let $(Y, d)$ be a *metric space*. Give $\mathcal{C}(X, Y)$ the **topology of compact convergence**; let $\mathcal{F}$ be a subset of $\mathcal{C}(X, Y)$. 
> 
> 1. If $\mathcal{F}$ is **equicontinuous** *under $d$* and the set
> $$
> \begin{align*}
> F_{a} &= \set{f(a): f \in \mathcal{F}}
> \end{align*}
> $$
> has **compact closure** for each $a \in X$, then $\mathcal{F}$ is *contained* in a **compact subspace** of $\mathcal{C}(X, Y).$
> 2. The **converse holds** if $X$ is **locally compact Hausdorff**.

^262108

- [[Metric Space]]
- [[Topology of Compact Convergence]]
- [[Equicontinuity]]
- [[Compactness]]
- [[Locally Compact Hausdorff Space]]

### Heine-Borel Property

- [[Heine-Borel Property for Topological Vector Space]]

![[sigma-Compactness#^7232d3]]

- [[sigma-Compactness]]

>[!important]
>Let $(\mathcal{X}, d)$ be a metric space. 
>
>$\mathcal{X}$ has a **Heine–Borel metric** which is *Cauchy locally identical* to $d$ *if and only if* it is **$\sigma$-compact**, **locally compact** and **complete.




-----------
##  Recommended Notes and References

- [[Metric Space]]
- [[Continuous Function]]
- [[Compactness]]
- [[Equicontinuity]]
- [[Pointwise Boundedness]]

- [[Heine-Borel Property for Topological Vector Space]]


- [[Topology Book by Munkres]]
- [[Real Analysis by Royden]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)