---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - Lp_space
topics:
  - functional_analysis
  - real_analysis
name: Lp Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  $L^p$ Space

>[!important] Definition
>Let $(X, \mathscr{F}, \mu)$ be a *measure space* and **$p\ge 1$**. 
>
>We denote by **$L^{p}(X, \mu)$** **the set of equivalence classes** of *measurable functions* which satisfy:
>$$
> \begin{align*}
> \lVert f \rVert_{p} &:= \left(\int_{X}\lvert f \rvert^{p}  d\mu\right)^{1 / p} < \infty
> \end{align*} 
>$$
>
>Here two functions are *equivalent* if they differ only on a set of *measure zero*.

- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]



## Explanation

>[!important] Riesz-Fisher Theorem
>Let $(X, \mathscr{F}, \mu)$ be a *measure space* and **$p\ge 1$**. 
>
>Then $L^p(X, \mu)$ is a **Banach space** with norm $$\lVert f \rVert_{p} = \left(\int_{X} |f|^p d\mu \right)^{1 / p}.$$

- [[Norm and Normed Space]]
- [[Minkowski Inequality]]
- [[Banach Space]]


## Example

>[!example]
>For $p=1$, $$L^1(X, \mu) := \left\{ f: X \to \mathbb{C} \text{ $\mu$-measurable}: \int_{X}|f| d\mu < \infty \right\} $$ is the space of **absolutely integrable functions** 

- [[Absolutely Convergent Integration]]

>[!example]
>For $p=\infty$, $$L^{\infty}(X, \mu) := \left\{ f: X \to \mathbb{C} \text{ $\mu$-measurable}: \text{ess }\sup_{X}|f| < \infty \right\} $$ is the space of **essentially bounded functions** 

- [[Bounded Function and Space of Bounded Functions]]

>[!example]
>For $p=2$, $$L^{2}(X, \mu) := \left\{ f: X \to \mathbb{C} \text{ $\mu$-measurable}: \left(\int_{X} f^2 d\mu\right)^{1 / 2} < \infty \right\} $$ is the space of **square integrable functions.**
>
>We can define the **inner product** in $L^2(X, \mu)$ as 
>$$
>\left\langle  f\,,\, g   \right\rangle_{L^2} := \int_{X} f\,\overline{g} \; d\mu
>$$
>This inner product is well defined using $\lVert \cdot \rVert_{2}$ based on **Parallelogram Law**:
>$$
>\left\langle  f\,,\,g    \right\rangle_{L^2} = \frac{1}{2} \left(\lVert f + g \rVert_{2} - \lVert f - g \rVert_{2} \right) 
>$$
>Thus $L^2(X, \mu)$ is a **Hilbert space.**

- [[Hilbert Space]]
- [[Pythagorean Theorem and Parallelogram Law]]






-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Banach Space]]

- [[Absolutely Convergent Integration]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)