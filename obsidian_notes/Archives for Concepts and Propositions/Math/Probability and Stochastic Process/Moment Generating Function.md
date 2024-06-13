---
tags:
  - concept
  - math/probability
keywords:
  - moment_generating_function
topics:
  - probability
name: Moment Generating Function of Random Variable
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Moment Generating Function of Random Variable


>[!important] Definition
>Given the *probability space* $(\Omega, \mathscr{F}, \mathcal{P})$ and suppose $X: (\Omega, \mathscr{F}) \rightarrow (\mathbb{R}, \mathcal{B})$ is a random variable, with *cumulative distribution function (c.d.f.)* $F_{X}.$
>
>The **moment generating function (M.G.F.)** of $X$, denoted as $M_{X}(\lambda)$,  is defined as 
>$$ 
> \begin{align*}
> M_{X}(\lambda) &:= \mathbb{E}_{\mathcal{P}}\left[ \exp \left(\lambda X\right) \right] \\
> &= \int_{\Omega}e^{\lambda X}d\mathcal{P},
> \end{align*}
>$$ 
>provided that the expectation exists for some $\lambda >0$. That is, there is an $h >0$ such that for all  $\lambda \in (-h, h)$, the above expectation exists.

- [[Expectation of Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]

>[!info]
>In general case, given the c.d.f. $F_{X}$, we can use [Riemann–Stieltjes integral](https://en.wikipedia.org/wiki/Riemann%E2%80%93Stieltjes_integral "Riemann–Stieltjes integral"), to compute the M.G.F.
>$$
>M_{X}(\lambda) := \int_{-\infty}^{+ \infty}e^{\lambda\, t}dF_{X}(t)
>$$

## Explanation

>[!important]
>Recall that the **Laplace transform** is defined as
>$$
>\mathcal{L}[f_{X}](s) := \int_{-\infty}^{+\infty}e^{-s\,t} f(t) dt
>$$
>Thus *the moment generating function* is **the Laplace transform of p.d.f.** $f_{X}$ when $\lambda = -s$
>$$
>M_{X}(\lambda) := \int_{-\infty}^{+ \infty}e^{\lambda\, t}f_{X}(t)dt = \mathcal{L}[f_{X}](-\lambda)
>$$

- [[Laplace Transform]]

>[!info]
>If we use *Riemann-Stieltjes integral* to define *the moment generating function*, we can also use **the Laplace-Stieljes transform** to replace *the Laplace transform*. 
>$$
>\{\mathcal{L}*F_{X}\}(s) := \int_{-\infty}^{+\infty}e^{-s\,t} dF(t)
>$$
>This results in the same conclusion: *M.G.F is the Laplace-Stieljes transform of c.d.f. $F_{X}$ with $\lambda = -s$*
>$$
>M_{X}(\lambda) := \int_{-\infty}^{+ \infty}e^{\lambda\, t}dF_{X}(t) = \{\mathcal{L}*F_{X}\}(-\lambda)
>$$


## Examples










-----------
##  Recommended Notes and References

- [[Random Element and Random Variable]]
- [[Probability Distribution of Random Variable]]

- [[Characteristic Function of Random Variable]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)