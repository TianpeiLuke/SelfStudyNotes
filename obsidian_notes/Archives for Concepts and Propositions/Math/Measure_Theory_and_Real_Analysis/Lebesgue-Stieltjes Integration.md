---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - lebesgue_stieltjes_integration
topics:
  - measure_theory
  - real_analysis
name: Lebesgue-Stieltjes Integration
date of note: 2024-06-06
---

## Concept Definition

>[!important]
>**Name**: Lebesgue-Stieltjes Integration

>[!important] Thoerem
>Let $F : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** and **absolutely continuous** function. Let $\mathcal{B}[\mathbb{R}]$ be the *Borel $\sigma$-algebra* on $\mathbb{R}$.
>
>Then for any $E\in \mathcal{B}[\mathbb{R}]$, the **Lebesgue-Stieltjes measure** of $E$ can be represented in the following form
>$$
>\mu_{F}(E) = \int_{E} F'(x)\,dx,  
>$$
>where $F'(x)$ is the *first-order derivative* of $F$ and the RHS is with respect to **Lebesgue measure**.

^193b27

- [[Absolutely Continuous Function]]
- [[Monotone Differentiation Theorem]]
- [[Second Fundamental Theorem of Calculus Absolutely Continuous]]

>[!important] Proposition
>Let $F : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** and **absolutely continuous** function. Let $\mathcal{B}[\mathbb{R}]$ be the *Borel $\sigma$-algebra* on $\mathbb{R}$.
>
>For any **unsigned Borel measurable** function $f: \mathbb{R} \to \mathbb{R}$, we have
>$$
>\int_{\mathbb{R}} f\,d\mu_{F} = \int_{\mathbb{R}} f\,F'\,dx.
>$$

>[!important] Definition
>From above proposition, we define the **Lebesgue-Stieltjes Integral** of $f$ *with respect to* $F$ as
>$$
>\int_{\mathbb{R}} f\,dF := \int_{\mathbb{R}} f\,d\mu_{F}
>$$



## Explanation

>[!info]
>For _monotone and **absolutely continuous function**_ $F$, the corresponding *Lebesgue-Stieltjes measure* is **absolutely continuous** with respect to *Lebesgue measure*.
>$$\mu_{F} \ll m.$$

- [[Lebesgue-Stieltjes Measure]]
- [[Lebesgue Measure]]
- [[Absolute Continuity for Measures]]


- [[Riemann–Stieltjes Integration]]

## Integration by Parts

>[!important] Proposition
>Let $F : \mathbb{R} \to \mathbb{R}$ and $G : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** and **continuous** function. 
>
>Then the **integration by parts formula** holds
>$$
>\int_{[a,b]} F\,dG =  - \int_{\mathbb{R}} G\,dF + F(b)G(b) - F(a)G(a)
>$$
>for any close interval $[a.b] \subset \mathbb{R}.$



## Expectation with respect to CDF

![[Expectation of Random Variable#^e97480]]

- [[Expectation of Random Variable]]



-----------
##  Recommended Notes and References

- [[Pre-Measure]]
- [[Hahn-Kolmogorov Extension of Pre-measure]]
- [[Hahn-Kolmogorov Theorem]]

- [[Lebesgue Measure]]
- [[Riemann–Stieltjes Integration]]


- [[Introduction to Measure Theory by Tao]]
