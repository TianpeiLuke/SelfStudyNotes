---
tags:
  - concept
  - math/probability
keywords:
  - probability_space
topics:
  - probability
name: Probability Space
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Probability Space $(\Omega, \mathscr{F}, \mathcal{P})$


>[!important] Definition
>A **probability space** is a triple $(\Omega, \mathscr{F}, \mathcal{P})$ where
> 
> - $\Omega$ is **the sample space** corresponding to **outcomes** of some (perhaps hypothetical) experiment.
> - $\mathscr{F}$ is **the $\sigma$-algebra** of subsets of $\Omega$. These subsets are called **events**.
> - $\mathcal{P}$ is a **probability measure**; that is, $\mathcal{P}: \mathscr{F} \mapsto [0,1]$ is a function with domain $\mathscr{F}$ and range $[0, 1]$ such that
> 1. **Non-Negative**: $\mathcal{P}(A)\ge 0$ for all $A\in \mathscr{F}$.
> 2. **Countably Additive**: If $\{A_{n}\}\subset \mathscr{F}$ are *disjoint*, then
> $$ 
> \begin{align*}
> \mathcal{P}\left(\bigcup_{n=1}^{\infty}A_{n}\right) &= \sum_{n=1}^{\infty}\mathcal{P}\left(A_{n}\right).
> \end{align*}
> $$
> 3. **Finiteness**: $\mathcal{P}(\Omega) = 1$.


>[!info]
>- Each element in $\Omega$ is called an **outcome** or a *sample point*.
>- A $\mathcal{P}$-measurable subset $A \subset \Omega$ is called an **event**.



## Explanation

>[!info]
>For regular probability measure $\mathcal{P}$ on Borel $\sigma$-algebra $\mathscr{F}$ with locally compact Hausdorff $\Omega$, we can find an **isomorphism** between $\mathcal{P}$ and **the mean (integral) operation** with respect to $\mathcal{P}$. This is the classical result from [[Riesz-Markov Representation Theorem]] 
>$$
>\mathcal{P} \mapsto \mathbb{E}_{ \mathcal{P} }\left[  \cdot \right] := \int_{\Omega} \cdot\, d\mathcal{P}
>$$ 
>
>Thus, under these conditions, we can write $$\mathcal{P}X := \mathbb{E}_{\mathcal{P}}\left[  X \right]$$ where $\mathcal{P}$ is treated as the **linear functional** (i.e. **mean functional**) on random variable (measurable function) $X$.

- [[Expectation of Random Variable]]



-----------
##  Recommended Notes and References

- [[sigma Algebra]]
- [[Finite and sigma-Finite Measure]]
- [[Measure Space and Countably Additive Measure]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)