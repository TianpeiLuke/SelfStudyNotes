---
tags:
  - concept
  - math/probability
keywords:
  - probability_distribution
topics:
  - probability
name: distribution of random variable
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Probability Distribution of Random Variable


>[!important] Definition
>Given the *probability space* $(\Omega, \mathscr{F}, \mathcal{P})$ and suppose $X: (\Omega, \mathscr{F}) \rightarrow (\Omega', \mathscr{B})$ is *measurable*, then the *set function*
>$$ 
> \begin{align*}
> \mathcal{P}_{X} &\equiv \mathcal{P}\,\circ\, X^{-1} \\
> \Rightarrow \mathcal{P}_{X}(B) &= \mathcal{P}(X^{-1}(B)) \quad \text{for all }B \in \mathscr{B}
> \end{align*}
>$$ 
>is called the **induced probability** or **the distribution** *for random variable $X$*. 

>[!important]
>Given random variable $X$, we obtain an **induced probability space** $(\Omega', \mathscr{B}, \mathcal{P}_X)$ on the *image set*.

## Explanation

>[!info] Compare distribution vs. probability measure:
>
>- **Distribution** of *random variable*
>	- directly related to **random variables**
>	- a probability measure on the **co-domain space** (e.g. $\mathbb{R}$) of the random variable
>	- many distribution can be induced by the same probability measure
>	- can be estimated from data
>- **Probability measure** of *event* 
>	- directly related to measurable subset of sample space, i.e. **events** 
>	- a probability measure on the sample space $\Omega$
>	- not directly estimated by data
>- **Distribution** is push-forward measure of **Probability measure** by **random variable**


>[!important]
>The *distribution* of *random variable* $X$ is **the push-forward measure** of $\mathcal{P}$ by the measurable map (i.e. random variable) $X$:
>$$
> \begin{align*}
> \mathcal{P}_{X} &= X_{\#}\mathcal{P}.
> \end{align*}
>$$ 

- [[Push-forward Measure and Push-forward Operator]]


-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Random Element and Random Variable]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)