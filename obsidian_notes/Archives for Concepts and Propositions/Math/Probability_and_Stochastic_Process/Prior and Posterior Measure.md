---
tags:
  - concept
  - math/probability
  - statistics/inference
keywords:
  - prior_measure
  - posterior_measure
topics:
  - probability
  - statistics/inference
name: Prior and Posterior Measure
date of note: 2024-06-28
---

## Concept Definition

>[!important]
>**Name**: Prior and Posterior Measure

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable sample space* and $(\Theta, \mathcal{B}(\Theta))$ be a *Borel measurable parameter space*. Let $X$ be random variable taking value in $\mathcal{X}$.
>
>Define a kernel function $$K: \Theta \times \mathscr{F} \to [0, \infty)$$ such that 
>- for each $\theta\in \Theta$, $K(\theta, \cdot)$ is a *probability measure* on  $(\mathcal{X}, \mathscr{F})$
>- for each $A \in \mathscr{F}$, $K(\cdot, A)$ is a *measurable function* on  $(\Theta, \mathcal{B}(\Theta))$.
>
>Denote $K(\theta, A)$ as $\mathcal{P}_{\theta}(A)$.
>
>A **prior measure** $\Pi$ is a probability measure on *parameter space* $(\Theta, \mathcal{B}(\Theta))$ . 
>
>- Define **joint distribution** of $\theta \in \Theta$ and $X \in \mathcal{X}$  as a *probability measure* on $(\Theta \times \mathcal{X}\;, \;\mathcal{B}(\Theta) \times\mathscr{F})$ by $$\mathcal{P}_{\Theta \times \mathcal{X}}(B \times A) = \int_{B}\mathcal{P}_{\theta}(A)\,d\Pi(\theta), \quad \forall A \in \mathscr{F}, \; B \in \mathcal{B}(\Theta).$$ 
>- The **marginal distribution** of $X \in \mathcal{X}$ is $$\mathcal{P}_{\mathcal{X}}(A) := \mathcal{P}_{\Theta \times \mathcal{X}}(\Theta \times A)$$ Note that $\mathcal{P}_{\mathcal{X}}$ is a *probability measure* on $(\mathcal{X}, \mathscr{F})$.
>  
>A **posterior distribution** of $\theta$ given $X$ is the *conditional probability* of $\theta$ given $X$. 
>
>Formally, define a new kernel function $$P: \mathcal{X} \times \mathcal{B}(\Theta) \to [0, \infty)$$ such that
>- for each $x\in \mathcal{X}$, $P(x, \cdot)$ is a *probability measure* on  $(\Theta, \mathcal{B}(\Theta))$
>- for each $B \in \mathcal{B}(\Theta)$, $P(\cdot, B)$ is a *measurable function* on  $(\mathcal{X}, \mathscr{F})$.
>- for any $A \in \mathscr{F}$ and $B \in \mathcal{B}(\Theta)$, the following equation holds $$\mathcal{P}_{\Theta \times \mathcal{X}}(B \times A) = \int_{A}\,P(x, B)\,d\mathcal{P}_{\mathcal{X}}(x),$$ where $\mathcal{P}_{\mathcal{X}}$ is the *marginal distribution* of $X$.
>
>Denote *posterior distribution* of $\theta$ given $X=x$ as $P(x, B) = \Pi(B | x)$.

^319070


- [[Markov Transition Kernel and Transition Function]]
- [[Conditional Probability]]
- [[Measurable Function]]
- [[Product sigma-Algebra]]
- [[Product Measure]]
- Ghosh, J. K., & Ramamoorthi, R. V. (2003). *Bayesian Nonparametrics* (2003rd edition). Springer. pp 15


## Explanation

>[!info]
>This definition provides an *equation* for the two kernels $\mathcal{P}_{\theta}(A)$ and $\Pi(B | x)$ as
>$$
>\mathcal{P}_{\Theta \times \mathcal{X}}(B \times A) = \int_{B}\mathcal{P}_{\theta}(A)\,d\Pi(\theta) = \int_{A}\,\Pi(B | x)\,d\mathcal{P}_{\mathcal{X}}(x)
>$$
>where $\mathcal{P}_{\Theta \times \mathcal{X}}$ is a *probability measure* on *product $\sigma$-algebra* $\mathcal{B}(\Theta) \times \mathscr{F}.$

## Bayes Theorem

![[Bayes Theorem#^da1cc6]]


- [[Bayes Theorem]]


-----------
##  Recommended Notes and References

- [[Parametric Models]]
- [[Borel sigma Field]]
- [[Probability Space]]


- [[Probability and Measure by Billingsley]]
- [[Mathematical Statistics by Shao]] pp 231
- Ghosh, J. K., & Ramamoorthi, R. V. (2003). *Bayesian Nonparametrics* (2003rd edition). Springer. pp 15