---
tags:
  - concept
  - math/stochastic_process
  - math/probability
  - math/measure_theory
  - math/functional_analysis
keywords:
  - stochastic_process
topics:
  - stochastic_process
  - probability
  - measure_theory
  - functional_analysis
name: Stochastic Process
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Stochastic Process

>[!important] Definition
>Let  $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space, where $\mathscr{F}$ is the $\sigma$-algebra and $\mathcal{P}$ is the probability measure, and $(\mathcal{X}, \mathscr{B})$ be a measurable space. 
>
>
>A **stochastic process** is defined as a *collection of random variables* defined on a *common probability space*.
>
 >That is, a stochastic process is a *collection of $\mathcal{X}$-valued random variables*, which can be written as 
 >$$
 >\{ X_{t}, t\in T \},
 >$$
 >such that for each $t\in T$, 
>$$
>X_{t}: \Omega \to \mathcal{X}
>$$
>is $\mathscr{F} / \mathscr{B}$ *measurable*. 

^963482


>[!important] Alternative Definition
>We can consider a stochastic process as a $\mathcal{X}^{T}$-valued **random element**. That is, 
>$$
>X(\cdot): \Omega \to \mathcal{X}^{T} := \{ f: T \to \mathcal{X} \} 
>$$
>this alternative definition as a "**function-valued random variable**" in general requires *additional regularity* assumptions to be well-defined.

- [[Random Element and Random Variable]]

>[!important] Definition
>- The set $T$ is called the **index set** or **parameter set** of the stochastic process. Usually $T \subset \mathbb{R}$ represent the time. 
>- The codomain space $\mathcal{X}$ is called the **state space**.

>[!important] Definition
>A **sample function** is a *single outcome* of a stochastic process. Specifically for a stochastic process $\{ X(t, \omega), t\in T \}$, the map $$X(\cdot, \omega): T \to \mathcal{X}$$ for fixed $\omega \in \Omega$ is called a *sample function*, a **realization**, or, particularly when $T$ is interpreted as time, a **sample path** of the stochastic process. It can also be called a **trajectory**, a **path**, or a **path function**.

>[!important] Definition
>An **increment** of a stochastic process is the *difference* between two random variables of the same stochastic process. 
>
>For a stochastic process with an index set that can be interpreted as time, an increment is *how much the stochastic process changes* over a certain time period.

>[!important] Definition
>For a stochastic process as a random element $X: \Omega \to \mathcal{X}^T,$ the **law** *of stochastic process* $X$ is defined as the pushforward measure of $\mathcal{P}$ by $X$ on $(\mathcal{X}, \mathscr{B})$.
>$$
>\mathcal{P}_{X} = \mathcal{P} \circ X^{-1}
>$$

- [[Push-forward Measure and Push-forward Operator]]

## Explanation





-----------
##  Recommended Notes and References



- [[Random Element and Random Variable]]
- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[sigma Algebra]]

- Wikipedia [Stochastic process](https://en.wikipedia.org/wiki/Stochastic_process)