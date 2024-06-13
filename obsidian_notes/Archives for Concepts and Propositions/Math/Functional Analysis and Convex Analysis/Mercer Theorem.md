---
tags:
  - concept
  - math/functional_analysis
  - machine_learning/theory
keywords:
  - mercer_theorem
topics:
  - functional_analysis
  - machine_learning_theory
name: Mercer's Theorem
date of note: 2024-05-10
---

## Theorem

>[!important]
>**Name**:  Mercer's Theorem

>[!important] Theorem
>Suppose $\Omega$ is a **compact domain** and $T$ is a **positive Hilbert-Schmidt operator** on $L^2(\Omega)$. 
>
>If the **integral kernel** $K(\cdot, \cdot)$ is **continuous** on $\Omega \times \Omega$, then the **eigenfunction** $\varphi_k$ is **continuous** on $\Omega$ if $\lambda_k > 0$, and the expansion
>$$
> \begin{align*}
> K(x,y) &= \sum_{n=1}^{\infty}\lambda_{n}\varphi_n(x)\overline{\varphi_n(y)}
> \end{align*}
>$$
> converges **uniformly** on **compact sets.**

- [[Positive Semidefinite Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]

- [[Compact Operator]]
- [[Space of Bounded Linear Operators]]

## Explanation








-----------
##  Recommended Notes and References

- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]

- [[Bounded Linear Functional]]
- [[Lp Space]]
- [[Compactness]]

- [[Elements of Statistical Learning by Hastie]]
- [[Kernel Methods in Machine Learning by Hofmann]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)