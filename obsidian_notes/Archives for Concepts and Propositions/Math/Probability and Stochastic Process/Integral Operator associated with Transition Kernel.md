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
>**Name**:  Integral Operator associated with Transition Kernel

>[!important] Definition
> Given the transition kernel of Markov chain $K$, we can identify the *transition kernel* with an **integral operator** $$K: L^1(\mu) \to L^1(\mu)$$ as
>$$
>(Kh)(x) = \int h(y)\;K(x, dy), \quad \forall h \in L^1(\mu)
>$$

- [[Markov Chain Transition Kernel]]
- [[Compact Operator]]


## Understanding

- [[Covariance Operator]]








-----------
##  Recommended Notes and References

- [[Compact Operator]]
- [[Chapman-Kolmogorov Equation]]

- [[Markov Chain and Markov Process]]
- [[Markov Chain Transition Kernel]]