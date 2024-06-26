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
>The sequence $\{ f_{n} \}$ is said to be **tight** over $\mathcal{X}$ if for any $\epsilon >0$, there exists a subset $\mathcal{X}_{\epsilon} \subset \mathcal{X}$ such that $$\mu\left(\mathcal{X}_{\epsilon}\right) < \infty$$ has **finite measure**, and, for any $n \in \mathbb{N}$
>$$
> \int_{\mathcal{X} \setminus \mathcal{X}_{\epsilon} } |f_{n}|\,d\mu < \epsilon.
>$$

- [[Real Analysis by Royden]]  pp 376
- [[Probability and Measure by Billingsley]] pp 336

## Explanation

>[!info]
>For a sequence of integrable functions $\{ f_{n} \}$, the sequence is **tight** if 
>$$
> (\forall \epsilon)\; (\exists \mathcal{X}_{\epsilon}:\, \mu\left(\mathcal{X}_{\epsilon}\right) < \infty) \quad \sup_{n}\,\int_{\mathcal{X}}  |f_{n}|\;\mathbb{1}\left\{ \mathcal{X} \setminus \mathcal{X}_{\epsilon}\right\}\,d\mu \le \epsilon
>$$
>That is
>$$
>\inf_{\mathcal{X}_{\epsilon}:\; \mu \left(\mathcal{X}_{\epsilon}\right) < \infty}\;\sup_{n}\,\int_{\mathcal{X}}  |f_{n}|\;\mathbb{1}\left\{ \mathcal{X} \setminus \mathcal{X}_{\epsilon}\right\}\,d\mu = 0
>$$

>[!important] 
>For **probability space** $(\Omega, \mathscr{F}, \mathcal{P})$, the **tighness definition** of random variables is **superfluous** as all subsets $\mathcal{X}_{\epsilon} \subset \mathcal{X}$ have finite measure. We can just choose $\mathcal{X}_{\epsilon} := \mathcal{X}.$





-----------
##  Recommended Notes and References

- [[Vitali Lp Convergence Theorem]]
- [[Uniform Integrable Family of Functions]]

- [[Dominated Convergence Theorem]]
- [[Absolutely Convergent Integration]]

- [[Inner Regularity]]
- [[Tightness of Measures]]


- [[Probability and Measure by Billingsley]] pp 336
- [[Real Analysis by Royden]]  pp 376
- [[Introduction to Stochastic Calculus by Klebaner]] pp 185
- Wikipedia [Uniform_integrability](https://en.wikipedia.org/wiki/Uniform_integrability)