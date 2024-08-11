---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - lambda_return
  - compound_update
topics:
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
name: lambda-Return Algorithm and Compound Update
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: lambda-Return  and Compound Update

![[Multi-Step Return and Multi-Step Temporal Difference Learning#^de8997]]

![[Multi-Step Return and Multi-Step Temporal Difference Learning#^b19bc5]]

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

>[!important] Definition
>The **$\lambda$-return** is defined as *weighted average* of all possible *$n$-step returns*, each weighted proportionally to $\lambda^{n-1}$ for $\lambda\in [0,1]$. That is,
>$$
>\begin{align*}
>G_{t}^{\lambda} &:= \left(1- \lambda\right)\,\sum_{n=1}^{\infty}\lambda^{n-1}\,G_{t:t+n}\\[5pt]
>&= \left(1-\lambda\right)G_{t:t+1} + \left(1-\lambda\right)\lambda\,G_{t:t+2} \,{+}\ldots{+}\,
>\end{align*}
>$$
>The weight fades by with each additional step. That is, the weight **geometrically decay**.
>

^63443d


![[lambda_return.png]]

>[!info]
>Note that by the **geometric series**
>$$
>\sum_{n=1}^{\infty}\lambda^{n-1} =  \frac{1}{1- \lambda}
>$$
>Thus
>$$
>\left(1- \lambda\right)\sum_{n=1}^{\infty}\lambda^{n-1} = 1
>$$

![[lambda_return_weight_decay.png]]

>[!info]
>After a *terminal state* has been reached, all subsequent n-step returns are equal to the **conventional return**, $G_{t}$.

>[!important] Definition
>We can separate the *post-termination terms* from the main term in **$\lambda$-return** as
>$$
>\begin{align*}
>G_{t}^{\lambda} &:= \left(1- \lambda\right)\,\sum_{n=1}^{T- t -1}\lambda^{n-1}\,G_{t:t+n} + \lambda^{T-t-1}G_{t} \\[5pt]
>&= \left(1-\lambda\right)G_{t:t+1} + \left(1-\lambda\right)\lambda\,G_{t:t+2} \,{+}\ldots{+}\,\left(1-\lambda\right)\lambda^{T-t -2}\,G_{t:T-1} + \lambda^{T-t-1}G_{t} 
>\end{align*}
>$$
>- When $\lambda = 1$, $$G_{t}^{1} := G_{t}.$$ Thus $\lambda$-return reduces to *conventional return*, which is implemented via **Monte Carlo methods.**
>- When $\lambda = 0$, $$G_{t}^{0} = G_{t:t+1}.$$  Thus $\lambda$-return becomes the *one-step return*, which is implemented in the **one-step temporal difference learning TD(0)**.

- [[Monte Carlo Prediction for Value Estimation]]
- [[Temporal Difference Learning]]

>[!important] Definition
>An update that *averages simpler component updates* is called a **compound update**.


## Offline $\lambda$-Return Algorithm

>[!important] Definition
>The **offline $\lambda$-return algorithm** is implemented with two phase
>- Phase 1: *during the episode*,  it makes *no update* on the value function $V_{t}$ or its weight $w_{t}$;
>- Phase 2: at the *end of episode*, a whole sequence of *offline updates* are made using $\lambda$-return as *target* 
>	- $$V_{t+1}(X_{t}) = V_{t}(X_{t}) + \alpha_{t}\left[ G_{t}^{\lambda} - V_{t}(X_{t}) \right] $$ or 
>	- via *semi-gradient TD update* $$w_{t+1} = w_{t} + \alpha_{t}\left[ G_{t}^{\lambda} - \hat{v}(X_{t}, w_{t}) \right]\,\nabla \hat{v}\left(X_{t}, w_{t}\right) $$

- [[Temporal Difference Learning]]
- [[Value Function Approximation as Supervised Learning]]
- [[Gradient Monte Carlo Method for Value Function Approximation]]
- [[Semi-Gradient Temporal Difference]]


## Explanation

>[!quote]
>Now we note that a valid update can be done not just toward any $n$-step return, but toward any **average of $n$-step returns** for *different* $n$s. For example, an update can be done toward a target that is half of a two-step return and half of a four-step return: $1 / 2 G_{t: t+ 2} + 1 / 2 G_{t : t+ 4}$. Any set of n-step returns can be averaged in this way, even an infinite set, as long as the **weights** on the component returns are positive and sum to 1. The **composite return** possesses an **error reduction property** similar to that of individual n-step returns (7.3) and thus can be used to construct updates with guaranteed convergence properties. Averaging produces a substantial new range of algorithms. For example, one could average one-step and infinite-step returns to obtain another way of interrelating TD and Monte Carlo methods. In principle, one could even average *experience-based updates* with *DP updates* to get a simple combination of *experience-based* and *model-based methods.*
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 288

>[!important]
>The **idea** behind $\lambda$-return is the **ensemble learning** or **bagging**, i.e. averaging multiple sequences of updates to *reduce the variance*. In deep learning, a similar approach is via **dropout algorithm**.

- [[Ensemble Learning]]
- [[Bootstrap Method]]
- [[Dropout Algorithm]]



-----------
##  Recommended Notes and References

- [[Value Function Approximation as Supervised Learning]]
- [[Gradient Monte Carlo Method for Value Function Approximation]]
- [[Semi-Gradient Temporal Difference]]
- [[Eligibility Traces]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]


- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]


- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 288 - 291