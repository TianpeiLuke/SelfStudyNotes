---
tags:
  - concept
  - math/probability
keywords:
  - conditional_expectation
topics:
  - probability
name: conditional expectation
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Conditional Expectation


>[!important] Proposition
>Let $(X, \mathscr{B}, \mu)$ be a *finite measure space*, $\mathscr{F}$ is a **sub-$\sigma$-algebra** of $\mathscr{B}$, and $\nu = \mu|_{\mathscr{F}}$ is the *restriction* of $\mu$ on sub-$\sigma$-algebra $\mathscr{F}.$
>
 >If $f\in L^{1}(X, \mu)$, there exists $g\in L^{1}(X, \nu)$ (thus $g$ is *$\mathscr{F}$-measureable*) such that 
 >$$\int_{E} f d\mu = \int_{E} g d\nu$$ for all $E\in  \mathscr{F}$.
 >
 >If $g'$ is another such function, then $$g= g', \; \nu\text{-a.e.}$$ 

>[!info]
>By definition, the conditional expectation is **the Radon-Nikodym derivative** of $\nu$ with respect to $\mu$.

- [[Radon-Nikodym Derivative]]
- [[Lebesgue-Radon-Nikodym Theorem]]


>[!info]
>Let $(X, \mathscr{B}, \mu)$ is a probability space $(\Omega, \mathscr{A}, \mathcal{P})$, and $f := X$ as a random variable, the $\mathscr{F}$-measurable function $g$ is also a random variable, called the *conditional expectation of $X$ given $\mathscr{F}$.* 


>[!important] Definition
>Let  $(\Omega, \mathscr{A}, \mathcal{P})$ be a probability space with a *sub-algebra* $\mathscr{F} \subset \mathscr{A}$, and $X \in L^1(\Omega, \mathcal{P})$ be an *integrable* random variable on $\mathscr{A}$.   
>
>There exists an *unique random variable* $\mathbb{E}_{}\left[ X | \mathscr{F} \right]$,  called **the conditional expectation** of $X$ *given sub-algebra* $\mathscr{F}$, having these two properties: 
>- $\mathbb{E}\left[ X | \mathscr{F} \right]$  is *$\mathscr{F}$-measurable*, and *integrable*, i.e.
>$$
>\mathbb{E}\left[ X | \mathscr{F} \right] \in L^1(\Omega, \mathcal{P}|_{\mathscr{F}})
>$$
>- $\mathbb{E}\left[ X | \mathscr{F} \right]$ satisfies the following **functional equation**
>$$
>\begin{align*}
> \int_{A} X \; d\mathcal{P} = \int_{A} \mathbb{E}\left[ X | \mathscr{F} \right]\; d\mathcal{P}|_{\mathscr{F}}, \quad \forall A \in \mathscr{F}.
\end{align*}
>$$

- [[Expectation of Random Variable]]
- [[Probability and Measure by Billingsley]]


## Explanation

>[!important]
>It is easy to define
>$$
>\mathbb{E}_{ p }\left[  X | A \right]
>$$
>for a given set $A$, but the **conditional expectation** is conditioning on a **random variable (measurable function)** not a fixed set.
>
>This is the reason why we have to rely on **filtration**.





-----------
##  Recommended Notes and References

- [[Expectation of Random Variable]]
- [[Probability Space]]
- [[Random Element and Random Variable]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)