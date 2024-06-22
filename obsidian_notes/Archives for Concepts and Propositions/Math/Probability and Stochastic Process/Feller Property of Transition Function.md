---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning_models/mc
keywords:
  - transition_function
  - feller_property
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_models
name: Feller Property of Transition Function
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Feller Property of Transition Function

>[!important] Definition
> If for any *bounded continuous function* $f(x)$, the function
> $$
> (t, z) \to \left( T_{t, t+h}\,f\right)(z) := \int_{\mathcal{X}}f(y)\;p(t, z, t+h, dy)
> $$
>is **continuous**, for any $h >0$, then we say  that the *transition function* $p$ (or, the corresponding *Markov process*) satisfies **the Feller property.**

- [[Space of Bounded Continuous Function]]
- [[Semigroup associated with Transition Function]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 23

## Explanation




## Generator of Markov Process

- [[Infinitesimal Generator of Markov Process]]




-----------
##  Recommended Notes and References


- [[Space of Bounded Continuous Function]]
- [[Semigroup associated with Transition Function]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
