---
tags:
  - concept
  - math/measure_theory
keywords:
  - tail_support
  - width
topics:
  - measure_theory
name: Tail Support and Width
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**: Tail Support and Width


>[!important] Defintion
> Let $$E_{n,m} := \set{x \in X: | f_n(x) - f(x) | \ge 1/m}.$$ 
> Define **the $N$-th tail support set** as 
>$$ 
> \begin{align*}
> T_{N,m} &:= \set{x \in X: | f_n(x) - f(x) | \ge 1/m,\;\;\exists n\ge N}\\ 
> &= \bigcup_{n\ge N}E_{n,m} \\
> &:= \sup_{n \ge N} E_{n, m}.
> \end{align*}
> $$ 

- [[Supremum and Infimum of Sets]]
- [[Limits of Sets]]


>[!important] Definition
>Also  let $\mu(E_{n,m})$ be the **width** of **$n$-th event** $\mathbb{1}(E_{n, m})$.  
>

>[!info]
>Note that $T_{N,m}\supseteq T_{N+1,m}$ is **monotone nonincreasing** and  $T_{N,m}\subseteq T_{N,m+1}$ is **monotone nondecreasing**.



## Explanation






-----------
##  Recommended Notes and References

- [[sigma Algebra]]
- [[Measure Space and Countably Additive Measure]]