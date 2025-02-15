---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - lebesgue_stieltjes_measure
topics:
  - measure_theory
  - real_analysis
name: Lebesgue-Stieltjes Measure
date of note: 2024-06-06
---

## Concept Definition

>[!important]
>**Name**: Lebesgue-Stieltjes Measure

>[!important] Theorem
>Let $F : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** function, and define the left and right limits 
>$$F_{-}(x) := \sup_{y < x}\,F (y);\quad F_{+}(x) := \inf_{y > x}F (y),$$ thus one has 
>$$F_{-}(x) \le F (x) \le F_{+}(x)$$ 
>for all $x$. Let $\mathcal{B}[\mathbb{R}]$ be the *Borel $\sigma$-algebra* on $\mathbb{R}$. 
>
>Then there exists a **unique Borel measure** $\mu_{F} : \mathcal{B}[\mathbb{R}] \to [0, +\infty]$ such that
>- for all $− \infty < b < a < +\infty,$
>$$
>\begin{align*}
>\mu_{F}([a,b]) &= F_{+}(b) - F_{-}(a)\\
>\mu_{F}([a,b)) &= F_{-}(b) - F_{-}(a)\\
>\mu_{F}((a,b]) &= F_{+}(b) - F_{+}(a)\\
>\mu_{F}((a,b)) &= F_{-}(b) - F_{+}(a)
>\end{align*}
>$$ 
>- and 
>  $$\mu_{F} (\{a\}) = F+(a) − F−(a)$$ 
>  for all $a \in \mathbb{R}.$

>[!important] Definition
>The measure $\mu_{F}: \mathcal{B}[\mathbb{R}] \to [0, +\infty]$ given by above theorem is called  the **Lebesgue-Stieltjes measure.**


## Explanation

>[!info]
>In some text, the measure $\mu_{F}$ is defined when $F$ is **right-continuous**, i.e. $$F = F_{+}.$$

## Proof of Existence

- [[Introduction to Measure Theory by Tao]] pp189

- [[Boolean Algebra Generated by Sets]]
- [[Finitely Additive Measure]]

- [[Pre-Measure]]
- [[Hahn-Kolmogorov Theorem]]


## Properties

>[!important] Proposition
>For every **monotone** function $F: \mathbb{R} \to \mathbb{R}$,  the **Lebesgue-Stieltjes measure** $\mu_{F}$ with respect to $F$ is a **Radon measure** on $\mathbb{R}$.
>
>*Conversely*, if $\mu$ is a **Radon measure** on $\mathbb{R}$, then there exists a **monotone** function $F: \mathbb{R} \to \mathbb{R}$, such that $$\mu = \mu_{F}.$$

- [[Radon Measure]]

>[!important]
>In the special case when $$F_{+}(-\infty) = 0$$ and $$F_{-}(+\infty) = 1,$$ then $\mu_{F}$ is a **probability measure**.
>
>$$F_{+}(x) = μF ((−\infty, x])$$ is known as the **cumulative distribution function** *of* $\mu_{F}$.

- [[Cumulative Distribution Function of Random Variable]]

## Lebesgue Measure


>[!important] Proposition
>If $F: \mathbb{R} \to \mathbb{R}$ is an **identity function**, i.e. $$F(x) = x,$$ then $$\mu_{F} = m$$ is equal to the **Lebesgue measure**.

- [[Lebesgue Measure]]




-----------
##  Recommended Notes and References


- [[Hahn-Kolmogorov Extension of Pre-measure]]

- [[Lebesgue-Stieltjes Integration]]

- [[Lebesgue Measure]]
- [[Riemann–Stieltjes Integration]]


- [[Introduction to Measure Theory by Tao]]
