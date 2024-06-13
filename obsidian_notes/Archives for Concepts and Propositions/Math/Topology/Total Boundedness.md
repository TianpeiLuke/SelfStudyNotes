---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - total_boundedness
topics:
  - functional_analysis
  - topology
name: total boundedness
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Total Boundedness


>[!important] Definition
>A metric space $(X, d)$ is said to be **totally bounded** if for every $\epsilon > 0$, there is a *finite covering* of $X$ by *$\epsilon$-balls*.

- [[Metric Space]]
- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Covering Number of Metric Space]]

## Explanation

>[!info]
>In other word, $(X, d)$ is **totally bounded** if and only if for any $\epsilon>0$, the **covering number** of the whole set is finite.

- [[Covering Number of Metric Space]]


## Compactness 

>[!important]
>A **precompact metric space** is *totally bounded*.

- [[Pre-Compactness]]
- [[Compactness]]

>[!important] Proposition
>A **metric space** $(X, d)$ is **compact** *if and only if* it is **totally bounded** and **complete**.

- [[Complete Metric Space]]
- [[Compactness]]

>[!info]
>For a subset $E$ of a metric space $(X, d)$,  the following are **equivalent**:
>- $E$ is **totally bounded** and **complete**.
>- **Bolzano-Weierstrass Property**: *Every sequence* in $E$ has **convergent subsequence.**
>- **Heine-Borel Property **: $E$ is **compact**, i.e. every open cover of $E$ has a finite subcover.

- [[Bolzano-Weierstrass Theorem]]
- [[Heine-Borel Property for Topological Vector Space]]

## Equicontinuous

>[!important] Proposition
>Let $X$ be a *space*; let $(Y, d)$ be a **metric space**. 
>
>If the subset $\mathscr{F}$ of $\mathcal{C}(X, Y)$ is **totally bounded** under the **uniform metric** corresponding to $d$, then $\mathscr{F}$ is **equicontinuous under $d$**.

- [[Uniform Topology on Metric Spaces]]
- [[Equicontinuity]]


>[!important] Proposition
>Let $X$ be a space; let $(Y, d)$ be a **metric space**; assume $X$ and $Y$ are **compact**. 
>
>If the subset $\mathscr{F}$ of $\mathcal{C}(X, Y)$ is **equicontinuous** *under $d$*, then $\mathscr{F}$ is **totally bounded** under the **uniform** and **sup** *metrics* corresponding to $d$.

- [[Uniform Topology on Metric Spaces]]
- [[Sup Metric on Space of Bounded Functions]]
- [[Compactness]]




-----------
##  Recommended Notes and References

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Covering Number of Metric Space]]

- [[Covering of Set and Open Covering of Topological Set]]
- [[Compactness]]
- [[Metric Space]]

- [[Complete Metric Space and Function Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)

- [[Topology Book by Munkres]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]