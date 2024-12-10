---
tags:
  - concept
  - math/probability
  - math/real_analysis
keywords:
  - borel_cantelli_lemma
topics:
  - probability
  - real_analysis
name: Borel-Cantelli Lemma
date of note: 2024-05-22
---

## Theorem

>[!important]
>**Name**: Borel-Cantelli Lemma

>[!important] Theorem (Borel-Cantelli Lemma)
>Let $\set{A_{n}}$ be any events. If 
>$$
> \begin{align*}
> \sum_{n}\mathcal{P}(A_{n})<\infty,
> \end{align*}
>$$  
>then
>$$
> \begin{align*}
> \mathcal{P}\left\{ \limsup\limits_{n\rightarrow \infty} A_{n}  \right\}  \equiv \mathcal{P}\left[ A_{n} \text{ i.o.} \right] = 0
> \end{align*}
>$$ 
> where "$i.o$" means **infinitely often**.

- [[Limits of Sets]]
- [[Independence of Events]]


## Explanation

>[!info]
>$$
> \begin{align*}
> \mathcal{P}\left\{ \limsup\limits_{n\rightarrow \infty} A_{n}  \right\}  = \mathcal{P}\left\{ \bigcap_{k \in \mathbb{N}}\bigcup_{n \ge k} A_{n}  \right\}\equiv \mathcal{P}\left[ A_{n} \text{ i.o.} \right]
> \end{align*}
>$$ 

>[!important]
>The theorem can be generalized to general **finite measure**.

>[!important]
>The **Borel-Cantelli Lemma** *does not require any __independence__ between events.* 

>[!important]
>It states that **almost every outcome** $\omega$ in $\Omega$  is contained in **at most finitely many** of events $A_n$ 
>
>or equivalently, $\set{n: \omega \in A_n}$ is **finite** for *every* $\omega$.

>[!info]
>The *Borel-Cantelli Lemma* is used as the basis for *proofs* of **almost sure convergence**. 
>
>Define the event 
>$$A_{n} := \set{\omega \in \Omega: | X_n(\omega) - X(\omega) | > \epsilon}.$$ 
>Thus the *Borel-Cantelli Lemma* states that 
>$$
>\mathcal{P}\left\{ \limsup\limits_{n\rightarrow \infty} A_{n}  \right\} = \mathcal{P}\left\{ \omega \in \Omega: | X_n(\omega) - X(\omega) | > \epsilon, \quad (\forall\, k \in \mathbb{N}) (\exists\, n \ge k) \right\} = 0
>$$
>So the complement 
>$$
>\mathcal{P}\left\{ \omega \in \Omega: | X_n(\omega) - X(\omega) | \le \epsilon, \quad (\exists\, k \in \mathbb{N}) (\forall\, n \ge k) \right\} = 1
>$$
>Thus
>$$
>\mathcal{P}\left\{\omega: \lim_{ n \to \infty }X_{n}  = X \right\} = 1
>$$

- [[Pointwise Almost Everywhere Convergence]]


## Proof

>[!info]
>$$
> \begin{align*}
> \mathcal{P}\left\{ \limsup\limits_{n\rightarrow \infty} A_{n}  \right\}  &= \mathcal{P}\left\{ \inf_{k \ge 1}\bigcup_{n \ge k} A_{n}  \right\}\equiv \mathcal{P}\left[ A_{n} \text{ i.o.} \right] \\
> &= \lim_{ k \to \infty } \mathcal{P}\left\{\bigcup_{n \ge k} A_{n}  \right\} \quad \text{ since } \bigcup_{n \ge k} A_{n}  \text{ monotone decreasing}\\
> &= \lim_{ k \to \infty }\sum_{n \ge k} \mathcal{P}\left\{A_{n}  \right\}
> \end{align*}
>$$ 

>[!info]
>For each $k$, the term is **finite**, i.e.
>$$
>\sum_{n \ge k} \mathcal{P}\left\{A_{n}  \right\} \le \sum_{n}\mathcal{P}\left\{A_{n}  \right\}<\infty
>$$
>And it is *decreasing* as $k$ increases.
>
>Therefore, the sequence 
>$$
>\sum_{n \ge k} \mathcal{P}\left\{A_{n}  \right\}
>$$
>converges to $0$ as $k\to \infty$. Q.E.D.



-----------
##  Recommended Notes and References

- [[Limits of Sets]]
- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Independence of Events]]

- [[Algorithm Big-O Notations in Probability]]


- [[A Probability Path by Resnick]]
- [[Introduction to Measure Theory by Tao]]
- [[Probability and Measure by Billingsley]]