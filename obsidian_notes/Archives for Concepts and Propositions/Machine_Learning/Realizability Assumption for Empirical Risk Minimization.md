---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
keywords:
  - empirical_risk_minimization
  - realizability_assumption
topics:
  - machine_learning_theory
name: Realizability Assumption for Empirical Risk Minimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Realizability Assumption for Empirical Risk Minimization


>[!important] Definition
>The **realizability assumption** states that there exists $h^{*} \in \mathcal{H}$ such that the *generalization error*
>$$
>L_{\mathcal{P}}(h^{*}) = 0.
>$$
>For fixed $h^{*}$, by the *strong law of large numbers*, this means that
>$$
>L_{\mathcal{D}}(h^{*}) = \frac{1}{n}\sum_{i=1}^{n}f_{h,l}(X_{i}) = \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h(X_{i}) \neq l(X_{i})\} = 0,\quad  \mathcal{P}\text{-a.s.}
>$$

- [[Empirical Risk Minimization]]
- [[Kolmogorov Strong Law of Large Numbers]]


## Explanation


>[!info]
>Under the *realizability assumption*, the **zero training error** can be obtained within the hypothesis $\mathcal{H}$.

>[!info]
> That is, every ERM hypothesis has zero training error. 

>[!info]
> In the definition of **Probably Approximately Correct (PAC) Learning**, we assume the realizability assumption holds.

- [[PAC Learnable and Agnostic PAC Learnable]]



-----------
##  Recommended Notes and References

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Bounded Difference Inequality]]

- [[Empirical Process and Empirical Measure]]

- [[Understanding Machine Learning by Shalev-Shwartz]]

