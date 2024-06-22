---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - convergence_in_mean
  - convergence_in_l1_norm
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: convergence_in_lp_norm
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Convergence in $L^p$ norm


>[!important] Definition
>Let $(X, \mathscr{F},\mu)$ be *measure space*.
>
>We say that $f_n$ *converges* to $f$  **in $L^1$ norm** if the quantity 
>$$
> \begin{align*}
> \| f_n - f \|_{L^{1}(X)} =  \int_{X}| f_n(x) - f(x) | d\mu  \stackrel{n\rightarrow \infty}{\longrightarrow} 0.
> \end{align*}
> $$
>It is also called the **convergence in mean**. Denoted as $f_{n}\stackrel{L^{1}}{\rightarrow} f$.

- [[Lp Space]]

>[!important] Definition
>For $1 \le p < \infty$, we say that $f_n$ *converges* to $f$  **in $L^p$ norm** if the quantity 
>$$
> \begin{align*}
> \| f_n - f \|_{L^{p}(X)} =  \int_{X}| f_n(x) - f(x) |^{p} d\mu  \stackrel{n\rightarrow \infty}{\longrightarrow} 0.
> \end{align*}
> $$
>It is denoted as $f_{n}\stackrel{L^{p}}{\rightarrow} f$.

- [[Convergence in Norm]]
- [[Norm Topology]]
- [[Lp Space]]

>[!important] Definition
>For $p = \infty$, we say that $f_n$ *converges* to $f$  **in $L^{\infty}$ norm**  if the quantity 
>$$
> \begin{align*}
> \| f_n - f \|_{L^{\infty}(X)} =  \text{ess }\sup_{x\in X}| f_n(x) - f(x)|  \stackrel{n\rightarrow \infty}{\longrightarrow} 0.
> \end{align*}
> $$
>It is also called $f_{n}$ converges to $f$ **uniformly almost everywhere**. Denoted as $f_{n}\stackrel{L^{\infty}}{\rightarrow} f$.

- [[Uniformly Almost Everywhere Convergence]]

## Explanation


## Vitali $L^p$ Convergence Theorem

- [[Pointwise Almost Everywhere Convergence]]
- [[Tightness of Integrable Functions]]
- [[Uniform Integrable Family of Functions]]
- [[Vitali Lp Convergence Theorem]]




-----------
##  Recommended Notes and References

- [[Uniformly Almost Everywhere Convergence]]
- [[Convergence in Norm]]

- [[Vitali Lp Convergence Theorem]]


- [[Modes of Convergence]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)