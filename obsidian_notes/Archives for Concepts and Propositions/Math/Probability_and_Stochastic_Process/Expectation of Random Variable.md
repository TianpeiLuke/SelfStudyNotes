---
tags:
  - concept
  - math/probability
  - math/real_analysis
keywords:
  - expectation
topics:
  - probability
name: Expectation of Random Variable
date of note: 2024-05-13
---

## Concept Definition

>[!important]
>**Name**: Expectation of Random Variable

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space* and $X: \Omega \to \mathbb{R}$  be a random variable in $\mathscr{F}$.  
>
>The **expectation** of random variable $X$ is defined as the *Lebesgue integral*
>$$
>\mathbb{E}_{\mathcal{P}}\left[ X \right] := \int_{\Omega} X \, d\mathcal{P}
>$$



- [[Probability Space]]
- [[Random Element and Random Variable]]
- [[Absolutely Convergent Integration]]


## Explanation

>[!info]
>For *regular probability measure* $\mathcal{P}$ on *Borel $\sigma$-algebra* $\mathscr{F}$ with *locally compact Hausdorff* $\Omega$, we can find an **isomorphism** between $\mathcal{P}$ and **the mean (integral) operation** with respect to $\mathcal{P}$. This is the classical result from [[Riesz-Markov Representation Theorem]] 
>
>In particular, consider the **mean functional**: $\mathbb{E}_{\mathcal{P}}\left[ \cdot \right]: \mathcal{C}_{0}(\Omega) \to \mathbb{R}$, we can find an *isometric isomorphism* from $\mathcal{M}(\Omega) \to \mathcal{C}_{0}(\Omega)^{*}$
>$$
>\mathcal{P} \mapsto \mathbb{E}_{ \mathcal{P} }\left[  \cdot \right] := \int_{\Omega} \cdot\, d\mathcal{P}
>$$ 
>
>Thus, under these conditions, we can write $$\mathcal{P}X := \mathbb{E}_{\mathcal{P}}\left[  X \right]$$ where $\mathcal{P}$ is treated as the **linear functional** (i.e. **mean functional**) **acts** *on* random variable (i.e. continuous function) $X$.

- [[Probability Space]]
- [[Riesz-Markov Representation Theorem]]

### Riemann-Stieltjes Integration


>[!important] 
>Let $F: \mathbb{R} \to \mathbb{R}$ be the **cumulative distribution function** of real-valued *random variable* $X$, then the **expectation** of $X$ can be written as the **Riemann-Stieltjes integral** and the **Lebesgue-Stieltjes integral**
>$$
>\mathbb{E}_{ F }\left[  X \right] := \int_{\mathbb{R}} x\, dF(x) = \int_{\Omega} X\, d\mathcal{P}_{F}
>$$

^e97480

- [[Cumulative Distribution Function of Random Variable]]
- [[Riemann–Stieltjes Integration]]
- [[Lebesgue-Stieltjes Measure]]
- [[Lebesgue-Stieltjes Integration]]


## Properties

>[!important] Proposition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and  $X: \Omega \to \mathbb{R}_{+}$ be a *non-negative random variable*. Then
>$$
>\begin{align*}
>\mathbb{E}_{\mathcal{P}}\left[ X \right] &= \int_{0}^{+\infty} \mathcal{P}[ X \ge t ]dt
\end{align*}
>$$



-----------
##  Recommended Notes and References

- [[Random Element and Random Variable]]
- [[Probability Space]]
- [[Absolutely Convergent Integration]]
- [[Development of Integrations]]