---
tags:
  - concept
  - math/functional_analysis
  - math/probability
keywords:
  - cumulative_distribution_function
topics:
  - probability
  - measure_theory
name: cumulative distribution function of random variable
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  *Cumulative Distribution Function (C.D.F.)* of Random Variable


>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space*. Given any *random variable* (real-valued measurable function) $X : \Omega \rightarrow \mathbb{R}$, we define the **cumulative distribution function** $F : \mathbb{R} \rightarrow [0, \infty]$ of $X$ to be the function
>$$
> \begin{align*}
> F_{X}(\lambda) &:=  \mathcal{P}\left\{ X^{-1}(\left(\right. -\infty, \lambda \left]\right.)  \right\} = (\mathcal{P} \circ X^{-1})(\left(\right. -\infty, \lambda \left]\right.).
> \end{align*}
>$$ 

^3391ff


## Explanation


>[!info]
>The collection of all closed rays $(-\infty, \lambda]$ for any $\lambda\in \mathbb{R}$ forms a basis of topology on $\mathbb{R}$. We call it the **left ray topology**.
>- Any open interval can be formed by set difference between two closed rays. 
>- The **left ray topology** is another topology as compared to standard topology on $\mathbb{R}$.

>[!info]
> - The c.d.f. of random variable is a special form of [[Probability Distribution of Random Variable]]
> - Instead of any open set in $\mathbb{R}$, we only measure the *closed rays* $(-\infty, \lambda]$.
> - In other word, c.d.f. corresponds to a probability measure defined on the Borel set generated from the topology of left rays.


>[!important]
>Note that there is a one-to-one map from **c.d.f of $X$** to the **push-forward** measure $\nu$ of $\mathcal{P}$ by random variable $X$.
>$$
>F \mapsto \nu:= X_{\#}\mathcal{P},
>$$ 
>such that
>$$
>F(\lambda) := \nu((-\infty, \lambda]),
>$$ 
>where the measure $\nu$ is defined on the **Borel $\sigma$-algebra** $\mathcal{B}_{(-\infty,\lambda]}$ induced by **left-ray topology** on $\mathbb{R}.$


- [[Push-forward Measure and Push-forward Operator]]


## Lebesgue-Stieltjes measure

>[!important]
>Given the cumulative function $F$, we have  $$F_{+}(-\infty) = \inf_{y > -\infty}F (y) = 0$$ and $$F_{-}(+\infty) := \sup_{y < +\infty}\,F (y) = 1,$$  then we can define a **Lebesgue-Stieltjes measure** $\mu_{F}$ as in [[Lebesgue-Stieltjes Measure]]. 
>
>We can show that $\mu_{F}$ is a **probability measure**.
>
>Conversely, given a **Lebesgue-Stieltjes measure** $\mu_{F}$, we can define
>$$F_{+}(x) = \mu_{F}((−\infty, x])$$  as the **cumulative distribution function** *of* $\mu_{F}$.

- [[Lebesgue-Stieltjes Measure]]

>[!info]
>In other word, there exists an one-to-one correspondence between **c.d.f. of random variable** $X$ and the underlying **probability measure** $\mathcal{P}$.




-----------
##  Recommended Notes and References

- [[Expectation of Random Variable]]
- [[Probability Distribution of Random Variable]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)