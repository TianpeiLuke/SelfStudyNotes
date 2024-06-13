---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
  - statistics/concentration_inequality
keywords:
  - holder_inequality
topics:
  - functional_analysis
  - real_analysis
  - concentration_inequality
name: Hölder's Inequality
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Hölder's Inequality

>[!important] Hölder's Inequality
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and let $p ,q \in [1, +\infty]$ with $$\frac{1}{p} + \frac{1}{q} = 1.$$
>
>Then for **all measurable real (or complex) functions** $f$ and $g$ on $\mathcal{X}$,
>$$
>\begin{align*}
> \lVert f\,g \rVert_{1} \le \lVert f \rVert_{p}\, \lVert g \rVert_{q}.   
>\end{align*}
>$$
>
>If, in addition, $p, q \in (1, +\infty)$ and $f\in L^p(\mathcal{X}, \mu)$ and $g\in L^q(\mathcal{X}, \mu)$, then the **equality** holds for above *if and only if* $$|f|^p, \; |g|^{q} \text{ are linearly dependent in } L^1(\mathcal{X}, \mu).$$ This means that there exists some real number $\alpha, \beta \ge 0,$ not all zero, such that 
>$$
>\alpha \lvert f \rvert^{p} = \beta \lvert g \rvert^{q}, \quad \mu\text{-almost everywhere.}  
>$$

- [[Dual Normed Space and Dual Banach Space]]
- [[Lp Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]





## Explanation

>[!important]
>For random variables $X$ and $Y$, we have
>$$
>  \mathbb{E}_{ \mathcal{P} }\left[ \lvert X\,Y \rvert  \right] \le \left( \mathbb{E}_{ \mathcal{P} }\left[ \lVert X \rVert^p  \right] \right)^{1/p} \,\left( \mathbb{E}_{ \mathcal{P} }\left[ \lVert X \rVert^q  \right] \right)^{1/q}
>$$




## Example

>[!example]
>If $$p = q = \frac{1}{2},$$ we have the **Cauchy-Schwartz inequality**.

[[Cauchy-Schwartz Inequality]]

## Proof

- [[Young Inequality]]



-----------
##  Recommended Notes and References

- [[Jensen Inequality]]
- [[Cauchy-Schwartz Inequality]]


- [[Dual Normed Space and Dual Banach Space]]
- [[Vector Space over a Field]]
- [[Banach Space]]

- [[Absolutely Convergent Integration]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]


- Wikipedia [Hölder Inequality](https://en.wikipedia.org/wiki/H%C3%B6lder%27s_inequality)