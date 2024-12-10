---
tags:
  - concept
  - math/probability
keywords:
  - zero_one_law
topics:
  - probability
name: Borel Zero-One Law
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Borel Zero-One Law

>[!important] Theorem (Borel Zero-One Law)
>If $\set{A_{n}}$ is a sequence of **independent events**, then 
>$$
> \begin{align*}
> \mathcal{P}\left\{ \limsup\limits_{n\rightarrow\infty} A_{n} \right\}=\mathcal{P}\left[A_{n} \text{ i.o.} \right]  = \left\{\begin{array}{cc}
> 0 & \text{if } \sum_{n}\mathcal{P}(A_{n})<\infty\\ 
> 1 & \text{if } \sum_{n}\mathcal{P}(A_{n})=\infty
> \end{array}  \right.
> \end{align*}
>$$ 

- [[Independence of Events]]
- [[Borel-Cantelli Lemma]]
- [[Algorithm Big-O Notations in Probability]]

## Explanation




## Proof

>[!info]
>For $\sum_{n}\mathcal{P}(A_{n})<\infty$, we have the result directly from [[Borel-Cantelli Lemma]].

>[!info]
>For $\sum_{n}\mathcal{P}(A_{n})=\infty$, we see that
>$$
> \begin{align*}
> \mathcal{P}\set{ \limsup\limits_{n\rightarrow\infty} A_{n} }&= \mathcal{P}\left\{\bigcap_{k\ge 1}\bigcup_{n\ge k}A_{n}  \right\}\\
> &=1- \mathcal{P}\left\{ \bigcup_{k\ge 1}\bigcap_{n\ge k}A^{c}_{n}  \right\}\\
> &= 1- \lim\limits_{k\rightarrow \infty}\mathcal{P}\left\{ \bigcap_{n\ge k}A^{c}_{n}  \right\} \quad (\text{by upward convergence})\\
> &= 1- \lim\limits_{k\rightarrow \infty}\mathcal{P}\left\{\lim\limits_{m\rightarrow\infty}\downarrow\bigcap_{n=k}^{m}A^{c}_{n}  \right\}\\
> &= 1- \lim\limits_{k\rightarrow \infty}\lim\limits_{m\rightarrow \infty}\mathcal{P}\left\{\bigcap_{n=k}^{m}A^{c}_{n}  \right\}  \quad (\text{by downward convergence})\\
> &= 1- \lim\limits_{k\rightarrow \infty}\lim\limits_{m\rightarrow \infty}\left( \prod_{n=k}^{m}\mathcal{P}(A_{n}^{c}) \right)\\
> &= 1- \lim\limits_{k\rightarrow \infty}\lim\limits_{m\rightarrow \infty}\prod_{n=k}^{m}\left( 1-\mathcal{P}(A_{n}) \right).
> \end{align*}
>$$


>[!info]
> Thus it suffice to show that
>$$ 
> \begin{align*}
> \lim\limits_{k\rightarrow \infty}\lim\limits_{m\rightarrow \infty}\prod_{n=k}^{m}\left( 1-\mathcal{P}(A_{n}) \right) = 0.
> \end{align*}
>$$
>

>[!info]
> We use the inequality 
>$$ 
> \begin{align*}
> 1 - x&\le \exp(-x), \quad x\in (0,1)
> \end{align*}
>$$ 
> thus for each fixed $k \le m$
>$$ 
> \begin{align*}
> \lim\limits_{m\rightarrow \infty}\prod_{n=k}^{m}\left( 1-\mathcal{P}(A_{n}) \right) &\le \lim\limits_{m\rightarrow \infty}\prod_{n=k}^{m}\exp\left( - \mathcal{P}(A_{n}) \right) \\
>&= \lim_{m\rightarrow \infty}\exp\left(- \sum_{n=k}^{m}\mathcal{P}(A_{n}) \right)\\
> &= \exp(-\infty) = 0
> \end{align*}
>$$ 
> since $\sum_{n}\mathcal{P}(A_{n})=\infty$. 
> 
> Therefore $\lim\limits_{k\rightarrow \infty}\lim\limits_{m\rightarrow \infty}\prod_{n=k}^{m}\left( 1-\mathcal{P}(A_{n}) \right) = 0$. Q.E.D.


-----------
##  Recommended Notes and References

- [[Borel-Cantelli Lemma]]

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Independence of Events]]


- [[A Probability Path by Resnick]]
- [[Introduction to Measure Theory by Tao]]
- [[Probability and Measure by Billingsley]]