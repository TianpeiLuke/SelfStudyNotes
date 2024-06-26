---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - convergence_in_measure
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: convergence in measure
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Convergence in Measure


>[!important] Definition
>We say that $f_n$ *converges* to $f$  **in measure** if, for every $\epsilon> 0$,  the measures
>$$
> \begin{align*}
> \mu\left(\left\{ x \in X:  | f_n(x) - f(x) |  \ge \epsilon \right\} \right) \stackrel{n\rightarrow \infty}{\longrightarrow} 0.
> \end{align*} 
>$$ 
>
>Denoted as $f_{n}\stackrel{\mu}{\rightarrow} f$.



>[!important]
>**Name**:  Convergence in Probability

>[!info]
>In probability, we say $X_n$ *converges* to $X$  **in probability**, denoted as $X_{n}\stackrel{P}{\rightarrow} X$. 
>Here $X_n$ is a measurable function on probability space, which is called a **random variable**. 
>
>That is, 
>$$
>\lim\limits_{n\rightarrow 0}P\left(\left\{\omega: |X_n(\omega) - X(\omega)| \ge \epsilon \right\}\right) = 0, \quad \forall \epsilon >0
>$$

## Explanation





-----------
##  Recommended Notes and References

- [[Convergence in Lp norm]]
- [[Measure Space and Countably Additive Measure]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)