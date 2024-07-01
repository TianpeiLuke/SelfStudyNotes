---
tags:
  - concept
  - math/probability
  - statistics/inference
keywords:
  - bayes_theorem
topics:
  - probability
  - statistics/inference
name: Bayes Theorem
date of note: 2024-06-28
---

## Concept Definition

>[!important]
>**Name**: Bayes Theorem or Bayes Formula

>[!important] Bayes Theorem
>Let $A, B$ be events. 
>
>$$
>P(A | B) = \frac{P(B|A)\,P(A)}{P(B)}
>$$
>where both $P(A|B)$ and $P(B|A)$ are **conditional probabilities** and $P(A)$ and $P(B)$ are both **marginal probabilities.**

### Measure Theoretical Version

![[Prior and Posterior Measure#^319070]]

- [[Prior and Posterior Measure]]
- [[Markov Transition Kernel and Transition Function]]

>[!important] Bayes Theorem
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable sample space* and $(\Theta, \mathcal{B}(\Theta))$ be a *Borel measurable parameter space*. Let $X$ be random variable taking value in $\mathcal{X}$.
>
>Let $\Pi$ be a **prior measure**  on *parameter space* $(\Theta, \mathcal{B}(\Theta))$ , and $\mathcal{P}_{\theta}(\cdot)$ be the **conditional distribution** of $X$ given $\theta$.  
>
>Then
>- The **posterior distribution** of $\theta$ given $x$ is **dominated** by the *prior*, i.e. $$ \Pi(\cdot | x) \ll \Pi$$ 
>- Moreover, 
>$$
>\begin{align*}
> \Pi(B | x) &= \frac{\mathcal{P}_{\Theta \times \mathcal{X}}(B \times dx)}{\mathcal{P}_{\mathcal{X}}(dx)}\\[5pt]
> &= \dfrac{\int_{B}\mathcal{P}_{\theta}(dx)\,d\Pi(\theta)}{\mathcal{P}_{\mathcal{X}}(dx)}\\[5pt]
> &= \dfrac{\int_{B}\mathcal{P}_{\theta}(dx)\,d\Pi(\theta)}{\int_{\Theta }\mathcal{P}_{\theta}(dx)\,d\Pi(\theta)},
>\end{align*}
>$$
>for any $B \in \mathcal{B}(\Theta).$

^da1cc6

### Density Version


>[!important] Bayes Theorem (Density Version)
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable sample space* and $(\Theta, \mathcal{B}(\Theta))$ be a *Borel measurable parameter space*. Let $X$ be random variable taking value in $\mathcal{X}$.
>
>Let $\Pi$ be a **prior measure**  on *parameter space* $(\Theta, \mathcal{B}(\Theta))$ , and $\mathcal{P}_{\theta}(\cdot)$ be the **conditional distribution** of $X$ given $\theta$.  
>
>- Assume there exists a *$\sigma$-finite measure* on $(\Theta, \mathcal{B}(\Theta))$ such that the prior measure is dominated by $\nu$ $$\Pi \ll \nu.$$
>- Also assume that the *conditional probability* $\mathcal{P}_{\theta}(\cdot)$ is dominated by a *$\sigma$-finite measure* $m$ on $(\mathcal{X}, \mathscr{F})$ $$\mathcal{P}_{\theta}(\cdot) \ll m.$$ This means that the marginal distribution $\mathcal{P}_{\mathcal{X}} \ll m.$
>- Denote $$\pi_{\Theta}(\theta) := \frac{d\Pi}{d\nu}, \quad p_{\theta}(x) := \frac{d\mathcal{P}_{\theta}}{dm}, \quad p_{\mathcal{X}}(x) :=  \frac{d\mathcal{P}_{\mathcal{X}}}{dm}.$$
>
>
>Then 
>- The **posterior distribution** of $\theta$ given $x$ is **dominated** by the *prior*, i.e. $$ \Pi(\cdot | x) \ll \Pi$$ and $$\frac{d\Pi(\theta| x)}{d\Pi(\theta)} = \frac{ p_{\theta}(x)}{p_{\mathcal{X}}(x)}.$$
>
>
>- The **posterior density** *with respect to* $\nu$   is
>$$
>p(\theta | x) = \frac{d\Pi(\theta| x)}{d\nu(\theta)} = \frac{p_{\theta}(x)\,\pi_{\Theta}(\theta)}{p_{\mathcal{X}}(x)}.
>$$

- [[Prior and Posterior Measure]]
- [[Conditional Probability]]
- [[Radon-Nikodym Derivative]]
- [[Mathematical Statistics by Shao]] pp 232
- [[Fubini Theorem]]


## Explanation

>[!important]
>In the Bayesian (or epistemological) interpretation, *probability* measures a **"degree of belief"**. Bayes' theorem links **the degree of belief** in a proposition **before** and **after accounting for evidence**.

>[!important]
>In the **frequentist** interpretation, probability measures a **"proportion of outcomes".** For example, suppose an experiment is performed many times. $P(A)$ is the *proportion of outcomes* **with property** $A$ (the **prior**) and $P(B)$ is the *proportion* **with property $B$**.  $P(B | A)$ is the *proportion of outcomes* *with property $B$* **_out of_** outcomes *with property* $A$, and $P(A | B)$ is the *proportion of those* with $A$ **_out of_** those *with* $B$ (**the posterior**).
>
>The role of Bayes' theorem is best visualized with **tree diagrams**. The two diagrams **partition the same outcomes** by $A$ and $B$ in *opposite orders*, to obtain the **inverse probabilities**. Bayes' theorem *links the different partitionings*.





-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Finite and sigma-Finite Measure]]


- [[Mathematical Statistics by Shao]] pp 232
- Ghosal, S., & van der Vaart, A. W. (2017). _Fundamentals of nonparametric Bayesian inference_ (Vol. 44). Cambridge University Press. pp 7
- Ghosh, J. K., & Ramamoorthi, R. V. (2003). *Bayesian Nonparametrics* (2003rd edition). Springer. pp 15
- Wikipedia [Bayes%27_theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem)

