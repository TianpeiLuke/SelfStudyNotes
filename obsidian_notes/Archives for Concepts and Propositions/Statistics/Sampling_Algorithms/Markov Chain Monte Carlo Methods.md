---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - Markov_Chain
  - monte_carlo
  - markov_chain_monte_carlo
topics:
  - statistics/monte_carlo
name: Markov Chain Monte Carlo Methods
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Markov Chain Monte Carlo Methods

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be *measurable space*, and $X \in \mathcal{X}$ be a *random variable* in $\mathcal{X}$ with distribution $\pi$.
>
>For a *measurable function* $h: \mathcal{X} \to \mathbb{R}$, the **goal** is to estimate the expectation of $h$ with respect to $\pi$
>$$
>  \mathbb{E}_{ \pi }\left[ h(X) \right]
>$$
>
>The **Markov Chain Monte Carlo (MCMC)** methods estimate the expectation by generating a sequence of samples $(X_{1} \,{,}\ldots{,}\,X_{n})$ from a *mixed Markov chain* $(X_{k}, k=1 \,{,}\ldots{,}\,)$ whose *invariant measure* is $\pi$.
>$$
>\widehat{\mathbb{E}}_{ \pi }\left[ h(X) \right] := \frac{1}{n}\sum_{k=1}^{n}\,h(X_{k})
>$$

- [[Markov Chain and Markov Process]]
- [[Invariant Measure and Stationary Distribution]]
- [[Ergodic Theorem for Positive Recurrent Markov Process]]

## Explanation

>[!important]
>The key **principles** behind the **MCMC** are
>- the Markov chain $(X_{k})$ need to be **ergodic**  i.e. 
>	- the chain is **irreducible**, **positive recurrent** for discrete-state
>	- the chain is **$\mu$-irreducible**, **Harris recurrent** for continuous-state
>- the Markov chain need to be **mixed**, i.e. it reaches the stationary status where the probability of $X_{k} \in A$ is $\pi(A)$ *for all* $k$
>- the **invariant measure** $\pi$ of Markov chain should be the **target measure** with respect to which the expectation is evaluated.

- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]


## Comparison with Traditional Monte Carlo


>[!info]
>Compare to traditional Monte Carlo method such as [[Accept-Reject Sampling]], we see that

|                                       | **traditional Monte Carlo**                                                                                                                                                              | **Markov chain Monte Carlo**                                                                                                                                                                               |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| domain                                | $(\mathcal{X}, \mathscr{F})$                                                                                                                                                             | $(\mathcal{X}, \mathscr{F})$                                                                                                                                                                               |
| target measure                        | $\pi$                                                                                                                                                                                    | $\pi$                                                                                                                                                                                                      |
| target function                       | $h: \mathcal{X} \to \mathbb{R}$                                                                                                                                                          | $h: \mathcal{X} \to \mathbb{R}$                                                                                                                                                                            |
| target estimand                       | $$\mathbb{E}_{ \pi }\left[ h(X) \right]$$                                                                                                                                                | $$\mathbb{E}_{ \pi }\left[ h(X) \right]$$                                                                                                                                                                  |
| estimator                             | $$\frac{1}{n}\sum_{k=1}^{n}h(X_{k})$$                                                                                                                                                    | $$\frac{1}{n}\sum_{k=1}^{n}h(X_{k})$$                                                                                                                                                                      |
| **independence** of $X_{k}$           | $\checkmark$                                                                                                                                                                             | $\times$                                                                                                                                                                                                   |
| **identical distribution** of $X_{k}$ | $\checkmark$                                                                                                                                                                             | $\checkmark$                                                                                                                                                                                               |
| **generator** of sample               | the *generalized inverse* $\pi^{-1}$ of c.d.f. of $\pi$ $$\pi^{-1}(U)$$ or **transformation** $F$ or via rejection and importance reweighing process                                     | **ergodic Markov chain** (irreducible, positive) $(X_{k})$ with *transition kernel* $$K(x, A)$$ and the **invariant measure** is $\pi$                                                                     |
| **Analytical form** of $\pi$          | $\checkmark$                                                                                                                                                                             | $\times$                                                                                                                                                                                                   |
| $\mathcal{X}$ is high dimensional     | $\times$                                                                                                                                                                                 | $\checkmark$                                                                                                                                                                                               |
| When start using the sample?          | immediately                                                                                                                                                                              | when the Markov chain is **mixed**                                                                                                                                                                         |
| **consistency of estimation**         | [[Kolmogorov Strong Law of Large Numbers]]                                                                                                                                               | [[Ergodic Theorem for Positive Recurrent Markov Process]]                                                                                                                                                  |
| Related Approaches                    | - [[Accept-Reject Sampling]]<br>- [[Importance Sampling]]<br>- [[Sequential Importance Sampling]]<br>- [[Particle Filter or Sampling-Importance-Resampling]]<br>- [[Stochastic Gradient Descent Algorithm]]<br><br><br><br> | - [[Metropolis-Hastings Algorithm]]<br>- [[Gibbs Sampling]]<br>- [[Hamiltonian Monte Carlo]]<br>- [[Stochastic Gradient Hamiltonian Monte Carlo]]<br>- [[Langevin Dynamics and Langevin Sampling]]<br><br> |
|                                       |                                                                                                                                                                                          |                                                                                                                                                                                                            |





-----------
##  Recommended Notes and References


- [[Markov Chain and Markov Process]]
- [[Detailed Balance Equation]]
- [[Time-Reversible Markov Chain]]

- [[Gibbs Sampling]]
- [[Metropolis-Hastings Algorithm]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Monte Carlo Statistical Methods by Robert]] pp 226, 267 - 509
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 105

- [[Probabilistic Graphical Models by Koller]] pp 505 - 524
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]] pp 586 - 596
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429 - 459

- Wikipedia [Metropolis-Hastings_algorithm](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm)