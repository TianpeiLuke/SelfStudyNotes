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

>[!important] Definition: **Transition Kernel**
> A **transition kernel** (or **probability kernel**) is a function $K$ defined on $\mathcal{X} \times \mathcal{B}(\mathcal{X})$ such that 
> 1. $\forall x \in \mathcal{X}$,    $K(x, \cdot)$  is a **probability measure**;
> 2. $\forall A \in \mathcal{B}(\mathcal{X})$,    $K(\cdot, A)$ is a **measurable** function.

- $\mathcal{B}(\mathcal{X})$ is the Borel $\sigma$-Algebra. [[Borel sigma Field]]
- [[Probability Space]]
- [[Measurable Function]]
- [[Conditional Probability]]

## Understanding


>[!info] **Conditional Density Function**
The above definition of Transition Kernel can be used to define the **conditional density function** $K(x, y) = P(y | x)$:
> - Given a point $x \in \mathcal{X}$, $P(A|x)$ is a probability measure of set $A \in \mathcal{B}(\mathcal{X})$
> - Given a Borel set $A \in \mathcal{B}(\mathcal{X})$, $P(A | x)$ is a measurable function of $x$

- [[Conditional Probability]]

## Alternative Definition

>[!info] **Transition Kernel**
Define the **transition kernel** of Markov Chain as the *time-invariant* **transition probability**
> $$
> K(x, y)  := P(X_{t+1} = y | X_t = x).
> $$ 


>[!info] **$m$-Step Transition Probability**
> Then the **$m$-step transition probability** is defined as
> $$
> K^{m}(x, y) = P(X_{t+m} = y | X_t = x)
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





-----------
##  Recommended Notes and References

- [[Markov Chain and Markov Process]]

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Conditional Probability]]
- [[Conditional Expectation]]

- [[Monte Carlo Statistical Methods by Robert]]