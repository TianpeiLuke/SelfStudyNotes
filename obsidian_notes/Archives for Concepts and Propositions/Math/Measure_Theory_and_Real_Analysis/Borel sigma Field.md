---
tags:
  - concept
  - math/measure_theory
keywords:
  - sigma_field
  - Borel_set
topics:
  - measure_theory
name: Borel sigma field
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Borel $\sigma$-Algebra


>[!important] Definition
> Given a **topological space** $(\mathcal{X},\mathscr{T})$ with topology $\mathscr{T}$, a ***Borel $\sigma$-field*** (or, *Borel $\sigma$-algebra*} $\mathscr{B}$ is a non-empty collection of *subsets* in $\mathcal{X}$ such that :
> 1. $\mathscr{B}$ is a **$\sigma$-field**;
> 2. **Open and Closed set**:   
> 	- A **open set** $U \in \mathscr T$ is a *Borel set* in $\mathscr{B}$; 
> 	- also a **closed set** $C\equiv U^{c}$ is a *Borel set* in $\mathscr{B}$. 
> 1. **Countable union** of **Closed Set** denoted as "$F_{\sigma}$ set" is a *Borel set*, 
> $$
> F_{\sigma, \Lambda}= \bigcup_{\lambda\in \Lambda}C_{\lambda} \in \mathscr{B}
> $$
> 
> 4. **Countable intersection** of **open sets** denoted as "$G_{\delta}$ set" is a *Borel set*, 
>    $$
>  G_{\delta, \Lambda}= \bigcap_{\lambda\in \Lambda}U_{\lambda} \in \mathscr{B}.
>  $$  
> 
> We refer to the pair $(\mathcal{X}, \mathscr{F})$ of a set $\mathcal X$ *together* with a $\sigma$-algebra on that set as **a measurable space**.

- [[Set Operations]]


>[!important] Alternative Definition
>Given a **topological space** $(\mathcal{X},\mathscr{T})$ with topology $\mathscr{T}$,  a ***Borel $\sigma$-field*** (or, *Borel $\sigma$-algebra*} $\mathscr{B}$ is the *$\sigma$-algrebra generated by open sets* in $\mathscr{T}$. That is, 
>$$
>\mathscr{B} := \sigma(\mathscr{T}) = \left\langle \mathscr{T} \right\rangle.
>$$

- [[sigma Algebra Generated by Sets]]


>[!info]
>A subset in a *Borel $\sigma$-algebra* on $\mathcal{X}$ is called a **Borel set** or **Borel measurable**.
## Explanation

- The **Borel $\sigma$-algebra** lies in between, which concerns both ***algebraic*** and ***analytical** structure*. 


>[!info]
>- $F_{\sigma}$ set is **not closed** under topology $\mathscr T$; however, it can be *open set*
>- $G_{\delta}$ set is **not open** under topology $\mathscr T$; however, it can be *closed set*

## Compare to Lebesgue measure

>[!important]
>The Borel $\sigma$-algebra on Euclidean space $\mathbb{R}^n$ is **coarser** than *the Lebesgue $\sigma$-algebra*. 
>$$\mathscr{B}(\mathbb{R}^n) \subset \mathscr{L}(\mathbb{R}^n).$$

- [[Lebesgue Measure]]

>[!info]
>There exist **Jordan measurable** (and hence **Lebesgue measurable**) subsets of $\mathbb{R}^n$ which are **not Borel measurable**. 
>
>-- [[Introduction to Measure Theory by Tao]]

>[!info]
>Despite this demonstration that *not all Lebesgue measurable subsets are Borel measurable*, it is **remarkably difficult** (though not impossible)} to *exhibit a specific set that is not Borel measurable*. 
>
>Indeed, a large majority of the *explicitly constructable sets* that one actually encounters in practice tend to be *Borel measurable*, and one can view the property of Borel measurability intuitively as a kind of **"constructibility" property**.  
>
>A Borel $\sigma$-algebra is **large enough** to contain all subsets in $X$ that is of *"practical use"* in computing measures and integrations within $(0,1]$. 

>[!important]
>Show that **the Lebesgue $\sigma$-algebra** $\mathscr{L}(\mathbb{R}^d)$  on $\mathbb{R}^n$ is generated by **the union** of **the Borel $\sigma$-algebra** $\mathscr{B}(\mathbb{R}^d)$ and **the null $\sigma$-algebra.**

>[!important] Proposition
>The Lebesgue $\sigma$-algebra $\mathscr{L}(\mathbb{R}^d)$  on $\mathbb{R}^n$ is a **completion** of the Borel $\sigma$-algebra $\mathscr{B}(\mathbb{R}^n)$.

-  [[Introduction to Measure Theory by Tao]]




-----------
##  Recommended Notes and References

- [[sigma Algebra]]
- [[Boolean Algebra]]
- [[Closed Set]]
- [[Topology of Set]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)