---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning_models/mc
keywords:
  - transition_function
  - semigroup
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_models
name: Semigroup associated with Transition Function
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Semigroup associated with Transition Function

>[!important] Definition
> Denote $L^{\infty}(\mathcal{X})$ the space of all *essentially bounded Borel measurable functions* $f: \mathcal{X} \to \mathbb{R}$ with norm $$\lVert f \rVert_{\infty} := \text{ess }\sup_{x\in \mathcal{X}}|f(x)|.$$
> 
>Consider *linear mapping* $T_{s,t}: L^{\infty}(\mathcal{X}) \to L^{\infty}(\mathcal{X})$:
>$$
>\begin{align*}
> \left( T_{s,t}f \right)(x) =  \int_{\mathcal{X}}f(y)\;p(dy, t, x, s)
>\end{align*}
>$$
>where $p(A,t, x, s)$ is a *Markov transition function*.
>
>We have
>- $$\lVert T_{s, t} \rVert = 1$$
>- **Associativity**:  for all $0 \le s < t <u$, $$T_{s, t}\,T_{t, u} = T_{s, u}$$
>- Furthermore, we define $T_{t,t} = I$ *identity map*.
>
>The family $\left\{ T_{s,t} \right\}$ is called the **semigroup associated with the transition probability function** $p$ (or with the corresponding Markov process)

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Lp Space]]
- [[Group]]
- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 23

## Explanation

>[!important]
>We can interpret the linear mapping as 
>$$T_{s,t}\,f :=  \mathbb{E}_{ p }\left[ f(X_{t}) |\,X_{s} = \cdot \right] $$

## Feller Property

- [[Feller Property of Transition Function]]


## Infinitesimal Generator of Markov Process

- [[Infinitesimal Generator of Markov Process]]





-----------
##  Recommended Notes and References

- [[Group]]
- [[Chapman-Kolmogorov Equation]]

- [[Borel Measure]]

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]