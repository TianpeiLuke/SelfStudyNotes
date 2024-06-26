---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - pointwise_almost_everywhere_convergence
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: pointwise almost everywhere convergence
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Pointwise Almost Everywhere Convergence


>[!important] Definition
>We say that  $f_n$ *converges* to $f$ **pointwise almost everywhere** if, for *$\mu$-almost everywhere* $x \in X$, $f_n(x)$ converges to $f(x)$. It is denoted as $f_{n}\stackrel{a.e.}{\rightarrow} f$.
>
>In other words, there exists *a null set* $E$, ($\mu(E) = 0$) such that for any $x\in X \setminus E$ and any $\epsilon > 0$, there exists $N > 0$ (that *depends on $\epsilon$ and $x$*) such that for all $n \ge N$, $$|f_n(x) - f(x)| \leq  \epsilon.$$ 


>[!important]
>**Name**:  Almost Surely Convergence

>[!info]
>In probability space, we say $X_n$ *converges* to $X$  **almost surely** or **with probability 1**, denoted as $X_{n}\stackrel{a.s.}{\rightarrow} X$. 
>
>Here $X_n$ is a measurable function on probability space, which is called a **random variable**. 
>Equivalently, 
>$$
>P\left(\left\{\omega: \lim\limits_{n\rightarrow \infty}X_n(\omega) = X(\omega)  \right\}\right) = 1
>$$


## Explanation

>[!info]
>Let
>$$E_{n,\epsilon} := \set{x \in X: | f_n(x) - f(x) | \ge \epsilon}.$$ 
>Then the pointwise almost everywhere convergence is 
>$$
>\mu\left(\limsup_{n \to \infty}E_{n,\epsilon}\right) = 0
>$$
>for each $\epsilon >0$.

- [[Limits of Sets]]


-----------
##  Recommended Notes and References

- [[Pointwise Convergence]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Measure Space and Countably Additive Measure]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)