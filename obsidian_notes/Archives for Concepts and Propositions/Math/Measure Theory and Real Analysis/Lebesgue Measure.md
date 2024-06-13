---
tags:
  - concept
  - math/measure_theory
keywords:
  - lebesgue_measure
topics:
  - measure_theory
name: Lebesgue measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Lebesgue Measure $m$


>[!important] Definition
>A set $E\subset \mathbb{R}^{d}$ is **Lebesgue measureable** if and only if for any $\epsilon>0$, there exists *open set* $U$ that **contains** $E$ such that  $m^{*}(U \setminus  E)< \epsilon$. 

- $m^{*}$ is the [[Lebesgue Outer Measure]]

>[!important] Definition
>We refer $m(E)= m^{*}(E)$ as the **Lebesgue measure** of $E$, for $E$ is *Lebesgue measureable*. 


>[!important] Lemma
>The **Lebesgue measure**  $m: \mathscr{A} \rightarrow \mathbb{R}_{+}$, where $\mathscr{A}$ is $\sigma$-algebra *containing* *Borel sets*,  satisfies the following properties:
> 
>- $m(\emptyset) = 0$;
>- **Countably additivity**:  For any countable union of disjoint sets $\set{E_{i}}_{i\ge 1}$ in $\mathscr{A}$ 
>$$
> \begin{align*}
>  m\left(\bigcup_{i=1}^{\infty}E_{i}\right) =  \sum_{i=1}^{\infty}m(E_{i}).
> \end{align*}
>$$  
>
>This also infers the *Finitely-additivity*.

- [[Measure Space and Countably Additive Measure]]

## Explanation


## Criteria for Measurability

>[!important] Proposition
>The followings are **equivalent**:
>
>- $E$ is **Lebesgue measureable**.
>- **Outer approximation** by **open**. For every $\epsilon>0$, one can contain $E$ in an open set $U$ with $$m^{*}(U \setminus  E)\le \epsilon.$$
>- **Almost open.** For every $\epsilon>0$, one can find an open set $U$ such that  $$m^{*}(U\Delta E)\le \epsilon,$$ where $$U\Delta E = (U  \setminus  E)\cup (E  \setminus  U) = (U\cup E) \setminus  (U\cap E)$$ is the *symmetric difference*. 
>  
>  (In other words, $E$ *differs from an open set* by a set of *outer measure* at most $\epsilon$.)
>- **Inner approximation** by **closed**. For every $\epsilon>0$, one can find a *closed set* $F$ contained in $E$ with $$m^{*}(E  \setminus  F)\le \epsilon .$$
>- **Almost closed**. For every $\epsilon>0$, one can find a *closed set* $F$ such that $$m^{*}(E\Delta F)\le \epsilon.$$ 
>  
>  (In other words, $E$ differs from a *closed set* by a set of *outer measure* *at most* $\epsilon$.)
>- **Almost measurable**. For every $\epsilon>0$, one can find a *Lebesgue measurable* set $E_{\epsilon}$ such that $$m^{*}(E\Delta E_{\epsilon})\le \epsilon.$$ 
>  
>  (In other words, $E$ differs from a measurable set $E_{\epsilon}$ by a set of *outer measure at most* $\epsilon$.)

- [[Lebesgue Outer Measure]]


>[!important] Proposition (Carathéodory Criterion)
>Let $E\subset \mathbb{R}^{d}$, the followings are **equivalent**:
>
>- $E$ is **Lebesgue measurable**;
>- For every **elementary set** $A\subset \mathbb{R}^{d}$, one has $$m(A) = m^{*}(A \setminus  E) + m^{*}(A\cap E).$$
>- For every **box** $B$, one has $$|B| = m^{*}(B \setminus   E) + m^{*}(B\cap E).$$
>

- [[Elementary Measure]]
- [[Carathéodory Measurability]]

## Property

>[!important] Proposition (Inner regularity)
> Let $E \subset \mathbb{R}^d$ be **Lebesgue measurable**, then
>$$ 
> \begin{align*}
> m(E)& = \sup\left\{m(K):\; K\subset E, \; K \text{ is compact} \right\}
> \end{align*}
>$$ 

- [[Inner Regularity]]

>[!important] Proposition (Translation Invariance)
>If $E \subseteq \mathbb{R}^d$ is **Lebesgue measurable**, and for any $x \in \mathbb{R}^d$, the **translation of measure** by $x$ is defined 
>$$
>E + x = \{ x + v: v\in E \},
>$$
>then $E + x$ is Lebesgue measurable, and that $$m(E + x) = m(E).$$


>[!important] Proposition (Measure of Elementary Sets)
>If $A_{n} = I_{1} \,{\times}\ldots{\times}\,I_{n}$, then $A_{n}$ is **Lebesgue measurable** and
>  $$
>  m\left(A_{n}\right) = \prod_{i=1}^n \lvert I_{i} \rvert 
> $$


## Uniqueness of Lebesgue Measure


>[!important] Proposition (Uniqueness of Lebesgue Measure)
>**Lebesgue measure** $E \mapsto m(E)$ is **the only map** from *Lebesgue measurable sets* to $[0, +\infty]$ that obeys the following **axioms**:
>
>- **Empty set**  $m(\emptyset) = 0$.
>- **Countably additivity**:  For any *countable union* of *disjoint* Lebesgue measurable sets $\set{E_{i}}_{i\ge 1}$ in $\mathscr{A}$ 
>$$ 
> \begin{align*}
>  m\left(\bigcup_{i=1}^{\infty}E_{i}\right) =  \sum_{i=1}^{\infty}m(E_{i}).
> \end{align*}
>$$ 
>- **Translation invariance** If $E$ is Lebesgue measurable and $x \in \mathbb{R}^d$, then $$m(E + x) = m(E).$$
>- **Normalisation**  $$m([0, 1]^d) = 1.$$
>

>[!info]
>There exists **no Lebesgue measure in infinite dimensional space**.



## Compare to Borel Measure


>[!important]
>The **Lebesgue measure space** $(\mathbb{R}^d, \mathcal{L}[\mathbb{R}^d], m)$ is **complete**, but the **Borel measure space** $(\mathbb{R}^d, \mathcal{B}[\mathbb{R}^d], \mu)$ is **not**.

- [[Borel Measure]]
- [[Complete Measure Space]]



-----------
##  Recommended Notes and References

- [[Lebesgue Outer Measure]]