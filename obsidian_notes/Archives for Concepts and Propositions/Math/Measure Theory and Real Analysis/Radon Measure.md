---
tags:
  - concept
  - math/measure_theory
  - math/functional_analysis
keywords:
  - radon_measure
topics:
  - measure_theory
  - functional_analysis
name: Radon measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:   Radon Measure

>[!important] Definition
>Let $(X, \mathcal{B})$ be a measurable space, where $X$ is a *locally compact Hausdorff (LCH) space* and $\mathcal{B}$ is *Borel $\sigma$-algebra*. 
>
>A **Radon measure** $\mu$ on $X$ is a *Borel measure* that is 
> 
> 1. **finite** on *all **compact** subsets*; i.e. for any *compact subset* $K \subseteq X$, 
> $$
> \begin{align*}
> \mu(K) < \infty.
> \end{align*}
> $$
> 2. **outer regular** on **all Borel sets**; i.e. for any *Borel set* $E$ 
> $$
> \begin{align*}
> \mu(E) &= \inf\set{\mu(U): U \supseteq E , U \text{ is open}}.
> \end{align*}
> $$
> 3. **inner regular** on **all open sets**; i.e. for any *open set* $U$
> $$
> \begin{align*}
> \mu(U) &= \sup\set{\mu(K): K \subseteq U, K \text{ is compact and Borel}}.
> \end{align*}
> $$
> 

- [[Locally Compact Hausdorff Space]]
- [[Regular Borel Measure]]
- *Finite* on *compact sets*
- [[Outer Regularity]] on *Borel sets*
- [[Inner Regularity]] on *open sets*


## Explanation

>[!info]
>In many books, **Radon measure** is defined as the [[Regular Borel Measure]], e.g. [[Functional Analysis by Reed]]

>[!info]
>A **Baire measure** is a *Radon measure.*

- [[Baire Measure]]

>[!info]
>Radon measure is a **$\sigma$-finite measure.**

- [[Finite and sigma-Finite Measure]]

## Properties 

>[!important] Proposition
>A Radon measure is **inner regular** on *all of its $\sigma$-finite sets.*
>
>-- [source](https://sites.math.washington.edu/~farbod/teaching/cornell/math6210pdf/math6210Radon.pdf)

- [[Finite and sigma-Finite Measure]]

>[!info] Corollary
>1.  If a Radon measure is *$\sigma$-finite*, then it is **regular**. 
>2. If $X$ is *$\sigma$-compact*, **every Radon measure** on $X$ is *regular*.

- Note that $X$ is $\sigma$-compact if it is a *countable union* of *compact sets.*

- The following proposition shows that under *Radon measure*, a measurable set can be *approximated* by 
	- an *open set* from outside and a *closed set* from inside
	- a *$G_{\delta}$ set* from outside and a *$F_{\sigma}$ set* from inside

>[!info] Proposition
>Let $(X, \mathcal{B}, \mu)$ be a *$\sigma$-finite Radon measure space*, and let $E \in \mathcal{B}.$ Then
> 1. for any $\epsilon > 0$, there exist $U$ *open* and $F$ *closed* such that 
>    $$F \subset E \subset U\quad\text{  and  }\quad \mu(U \setminus E) < \epsilon.$$
> 2. there exist a *$F_{\sigma}$ set* $A := \bigcup_{n=1}^{\infty}F_{n}$, where each $F_{n}$ is *closed*, and a *$G_{\delta}$ set* $B := \bigcap_{n=1}^{\infty}G_{n}$, where each $G_{n}$ is *open* ($n \in \mathbb{N}$), such that 
>    $$A \subset E \subset G \quad \text{ and } \quad \mu(B \setminus A) = 0$$
> 


## Generalization

>[!info]
>Some books defines the Radon measure as
>1. **Inner Regular** on *open sets*
>2. **$\sigma$-finite** Borel measure.
>   
>The **outer regularity**  can be derived from *$\sigma$-finiteness* and *inner regularity*.






-----------
##  Recommended Notes and References

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Compactness]]

- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]