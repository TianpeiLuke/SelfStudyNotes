---
tags:
  - concept
  - math/probability
keywords:
  - probability_density
topics:
  - probability
name: probability density
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  *Density* and *Probability Density*


>[!important] Definition
>Suppose  $(X, \mathscr{F}, \mu)$ is a *measure space.* Define a measure $\nu$ on $\mathscr{F}$ that is *absolutely continuous* with respect to $\mu$,
>$$\nu \ll \mu.$$
>
>According to the integral representation of measure,
>$$
>\begin{align*}
>\nu(A) &= \int_{A} f_{\nu}\; d\mu, \qquad \forall A \in \mathscr{F},
\end{align*}
>$$
>where $f_{\nu}$ is a $\mu$-measurable function, called the **density** of $\nu$ *with respect to $\mu$*. The measure $\nu$ is said to have *density* $f_{\nu}$ with respect to $\mu$.

- [[Absolute Continuity for Measures]]
- [[Signed Measure defined via Integral]]
- [[Radon-Nikodym Derivative]]
- [[Lebesgue-Radon-Nikodym Theorem]]


>[!info]
>Change $(X, \mathscr{F}, \mu)$ to be a probability space $(\Omega, \mathscr{F}, \mathcal{P})$. $f_{\nu}$ is called the **probability density** of $\nu$ with respect to $\mathcal{P}$.
## Explanation

>[!info]
>Given $(\Omega, \mathscr{F}, \mathcal{P})$ and a random variable $X$ on $\mathscr{F}$. The *distribution* of $X$ is a push-forward measure on the *Borel measurable space* $(\mathbb{R}, \mathcal{B})$ $$\mathcal{P}_{X} := X_{\#}\mathcal{P} = \mathcal{P} \circ X^{-1}.$$ Then the **probability density** of **random variable** $X$, denoted $p_{X}$, is defined as the density of $\mathcal{P}_{X}$ with respect to *Lebesgue measure* $\mu$ on $\mathbb{R}$. 
>$$
>\mathcal{P}_{X}(\left(\right.-\infty,  a\left]\right.) = \int_{-\infty}^{a}p_{x}\,d\mu
>$$


- [[Probability Distribution of Random Variable]]
- [[Lebesgue Measure]]

- [[Lebesgue Density from Radon-Nikodym Derivative]]


-----------
##  Recommended Notes and References


- [[Radon-Nikodym Derivative]]
- [[Lebesgue-Radon-Nikodym Theorem]]
- [[Probability Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)