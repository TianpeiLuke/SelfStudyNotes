---
tags:
  - concept
  - math/differential_equation
  - math/stochastic_process
keywords: 
topics:
  - differential_equation
  - stochastic_process
name: Infinitesimal Generator of Markov Process
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Infinitesimal Generator of Markov Process

>[!important] Definition
>Let $(X_{t})$ be a *(time-homogeneous) Markov Process*. Denote the set $\mathcal{D}_{\mathcal{A}}(x)$ as the set of functions $f: \mathbb{R}^n \to \mathbb{R}$ that *the limit at $x$ exists*.
>
>The **(infinitesimal) generator** $\mathcal{A}$ of $X_{t}$ is a linear operator $\mathcal{A}: \mathcal{D}_{\mathcal{A}}(x) \to \mathcal{D}_{\mathcal{A}}(x)$ defined by 
>$$
>\begin{align*}
>\left( \mathcal{A}f \right)(x) &:= \lim_{ t \to 0_{+} }   \frac{\mathbb{E}\left[ f(X_{t}) | X_{0} =x \right] - f(x)}{t}.
>\end{align*}
>$$
>
>Denote $\mathcal{D}_{\mathcal{A}}$ be the space of all functions  $f: \mathbb{R}^n \to \mathbb{R}$ that *the limit exists for all $x\in \mathbb{R}^n$.

- [[Infinitesimal Generator of Stochastic Differential Equation]]

- [[Markov Chain and Markov Process]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 159

## Explanation





-----------
##  Recommended Notes and References


- [[Markov Chain and Markov Process]]

- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]



- Wikipedia [Infinitesimal_generator](https://en.wikipedia.org/wiki/Infinitesimal_generator_(stochastic_processes))