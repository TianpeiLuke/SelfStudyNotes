---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - tight_family_integrable_functions
topics:
  - real_analysis
  - functional_analysis
  - stochastic_process
name: Tight Family of Integrable Functions
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Tight Family of Integrable Functions

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\{ f_{n} \}$ be a *sequence of functions* on $\mathcal{X}$, each of which is *integrable* over $\mathcal{X}$, i.e. $$\{ f_{n} \} \subset L^1(\mathcal{X}, \mu).$$
>
>The sequence $\{ f_{n} \}$ is said to be **tight** over $\mathcal{X}$ if there exists a subset $\mathcal{X}_{0} \subset \mathcal{X}$ that has **finite measure**, and, for any $n \in \mathbb{N}$
>$$
> \int_{\mathcal{X} \setminus \mathcal{X}_{0} } |f_{n}|\,d\mu < \epsilon.
>$$

- [[Real Analysis by Royden]]  pp 376


## Explanation




-----------
##  Recommended Notes and References

- [[Vitali Convergence Theorem for Uniformly Integrable Tight Functions]]
- [[Uniform Integrable Family of Functions]]

- [[Dominated Convergence Theorem]]
- [[Absolutely Convergent Integration]]

- [[Continuous Functions that Vanish At Infinity]]



- [[Real Analysis by Royden]]  pp 376
- [[Introduction to Stochastic Calculus by Klebaner]] pp 185
- Wikipedia [Uniform_integrability](https://en.wikipedia.org/wiki/Uniform_integrability)