---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning_models/mc
keywords:
  - Markov_Chain
  - Transition_Kernel
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_models
name: Markov Chain
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Markov Chain Transition Kernel

>[!important] Definition: 
> A **transition kernel** (or **probability kernel**) is a function $K$ defined on $\mathcal{X} \times \mathcal{B}(\mathcal{X})$ such that 
> 1. $\forall x \in \mathcal{X}$,    $K(x, \cdot)$  is a **probability measure**;
> 2. $\forall A \in \mathcal{B}(\mathcal{X})$,    $K(\cdot, A)$ is a **measurable** function.

- $\mathcal{B}(\mathcal{X})$ is the Borel $\sigma$-Algebra. [[Borel sigma Field]]
- [[Probability Space]]
- [[Measurable Function]]
- [[Conditional Probability]]
- [[Monte Carlo Statistical Methods by Robert]]


## Understanding


>[!info] **Conditional Density Function**
The above definition of Transition Kernel can be used to define the **conditional density function** $K(x, y) = P(y | x)$:
> - Given a point $x \in \mathcal{X}$, $P(A|x)$ is a probability measure of set $A \in \mathcal{B}(\mathcal{X})$
> - Given a Borel set $A \in \mathcal{B}(\mathcal{X})$, $P(A | x)$ is a measurable function of $x$

- [[Conditional Probability]]

## Transition Function

>[!important]
>Let $(X_{t}, t \ge 0)$ be a **Markov process**. 
>
>The **transition function** $p$ is defined as the conditional probability of $X_{t} \in A$ given that $X_{s} = x$
>$$
>\begin{align*}
>p(A, t, x, s) := K(X_{s} = x,  A) = \mathcal{P}\left( X_{t} \in A | X_{s} = x \right)
>\end{align*}
>$$
>where $A\in \mathcal{B}(\mathcal{X}).$
>
>Without confusion, we *identifies* the *transition kernel* and *transition function* with the same notation $K$.


- [[Markov Chain and Markov Process]]
- [[Stochastic Process]]




>[!info] 
>For discrete-state Markov chain $X_{t}$, the **transition kernel** of Markov Chain can be simplified as the *time-invariant conditional probability mass function*
> $$
> K(x, y)  := \mathcal{P}(X_{t+1} = y | X_t = x).
> $$ 

>[!info] **$m$-Step Transition Probability**
> Then the **$m$-step transition probability** is defined as
> $$
> K^{m}(x, y) = \mathcal{P}(X_{t+m} = y | X_t = x)
> $$
> 


## Chapman-Kolmogorov Equation

- [[Chapman-Kolmogorov Equation]]

>[!info]
>In general, we can consider $K: L^1(\mu) \to L^1(\mu)$ as an **operator** on $L^1(\mu)$. 
>
>That is, we can define
>$$
>K\,h(x) := \int_{\mathcal{X}} h(y)\,K(x, dy)
>$$

## Forward and Backward Equation of SDE


- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 135



-----------
##  Recommended Notes and References

- [[Markov Chain and Markov Process]]

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Conditional Probability]]
- [[Conditional Expectation]]

- [[Monte Carlo Statistical Methods by Robert]]
- [[Introduction to Stochastic Calculus by Klebaner]]