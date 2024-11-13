---
tags:
  - concept
  - math/functional_analysis
keywords:
  - hilbert_schmidt_operator
topics:
  - functional_analysis
name: Hilbert-Schmidt Operator
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Hilbert-Schmidt Operator

>[!important] Definition
>An operator $T \in \mathcal{L}(\mathcal{H})$ is called  **Hilbert-Schmidt** *if and only if*
>$$
> \begin{align*}
> \text{tr}\left( T^{*}T \right) < \infty.
> \end{align*}
>$$

^76da12

>[!important] Definition
>The **family of all Hilbert-Schmidt operators** is denoted by $\mathcal{B}_2(\mathcal{H})$ or $\mathcal{B}_{HS}(\mathcal{H}).$


- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Trace of Positive Semi-Definite Operator]]

- [[Bounded Linear Operator and Norm of Operator]]
- [[Space of Hilbert-Schmidt Operators]]

## Explanation


>[!important] 
>A *Hilbert-Schmidt operator* $T$ on a *square integrable space* $L^2(M, \mu)$ is a **integral kernel operator**.
>
>In other word, for $T \in \mathcal{L}(\mathcal{H})$,  if $$\text{tr}\left( T^{*}T \right) < \infty,$$ then $T$ is a **compact operator**. 

- [[Compact Operator]]

>[!important]
>If, in particular, $\mathcal{H} = L^2(M, \mu)$, then $T$ can be written as the **integral kernel operator** 
>$$
> \begin{align*}
> (T f)(x) &= \int_{M}\, K(x, y)f(y)\; d\mu(y),
> \end{align*}
>$$ 

- [[Positive Definite Kernel]]



-----------
##  Recommended Notes and References

- [[Space of Hilbert-Schmidt Operators]]
- [[Space of Trace Class Operators]]
- [[Trace Class Operator]]

- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Trace of Positive Semi-Definite Operator]]

- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)