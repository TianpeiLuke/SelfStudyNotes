---
tags:
  - concept
  - math/stochastic_process
keywords:
  - gauss–markov_process
topics:
  - stochastic_process
name: Gauss–Markov Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Gauss–Markov Process

>[!important] Definition
>A **Gauss-Markov process** is a stochastic process that satisfies the requirements for both **Gaussian process** and **Markov process**.

- [[Markov Chain and Markov Process]]
- [[Gaussian Process]]


## Explanation


>[!important] 
>*Gauss-Markov processes* obey the **Langevin equation**.

- [[Langevin Equation]]


## Covariance 

>[!important]
>The **covariance function** $K$ for *Gauss-Markov processes* has the form 
>$$
>K(s, t) = A(\min\{ s, t \})\;B(\max\{s,  t\})
>$$

- [[Covariance Function of Gaussian Process]]

>[!example]
>Let $$A = \exp \left(t / 2\right), \quad B = \exp \left(- t / 2\right),$$ we have
>$$
>K(s, t) = \exp \left(\frac{\min\{ s, t \}}{2}\right)\,\exp \left(-\frac{\max\{ s, t \}}{2}\right).
>$$
>This corresponds to the covariance function of [[Ornstein–Uhlenbeck Process]]


## Wiener Process

>[!important]
>*Gauss-Markov process* can be derived from Wiener process $(W_{t})$.
>
>Let $$X_{t} := f(t)\,W_{g(t)}$$ where $g： T \to T$ is an **increasing function**. Then the *covariance function*
>$$
>\begin{align*}
>\mathbb{E}\left[  X_{t}\,X_{s} \right] &= f(t)\,f(s)\;\mathbb{E}\left[  W_{g(t)}\,W_{g(s)} \right] \\
>&= f(t)\,f(s)\;\min\{ g(t), g(s) \}
>\end{align*}
>$$
>It can be represented as the form above where 
>$$
>A = f\,g, \quad B = f
>$$
>
>*Conversely*, given $A$ and $B$ that determines the covariance function 
>$$
>K(s, t) = A(\min\{ s, t \})\;B(\max\{s,  t\})
>$$
>we can define $$f = A, \quad g = \frac{A}{B},$$ so that the corresponding process $$X(t) = A(t)\,W\left( \frac{A}{B}(t) \right)$$ is the *Gauss-Markov process* with given covariance function.

- [[Brownian Motion Wiener Process]]






-----------
##  Recommended Notes and References

- [[Markov Chain and Markov Process]]
- [[Gaussian Process]]

- [[Ornstein–Uhlenbeck Process]]
- [[Langevin Equation]]

- [[Elements of Statistical Learning by Hastie]]
- [[Lectures on Gaussian Processes by Lifshits]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]

- Wikipedia [Gauss-Markov process](https://en.wikipedia.org/wiki/Gauss%E2%80%93Markov_process)