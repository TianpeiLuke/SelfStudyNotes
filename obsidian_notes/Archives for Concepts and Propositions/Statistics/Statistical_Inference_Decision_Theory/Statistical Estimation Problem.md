---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - statistics/decision_theory
keywords:
  - point_estimation
  - statistical_estimation
topics:
  - statistics/decision_theory
  - statistics/estimation
name: Statistical Estimation Problem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Statistical Estimation Problem

![[Statistical Decision Problem#^1e4cc1]]

![[Statistical Decision Problem#^e4b559]]

![[Statistical Decision Problem#^36cede]]

>[!important] Definition
>Assume that the sample $X = (X_{1} \,{,}\ldots{,}\, X_{n})$ is from a *parametric model* $\{\mathcal{P}_{\theta}: \theta \in \Theta\}.$
>
>Suppose that we need a **decision on the value** of $\theta \in \Theta$, based on the sample $X$.
>
>- Consider the **action space** $(\Theta, \mathcal{B}(\Theta))$ be the Borel measurable space of $\Theta$
>-  A **decision rule** is a measurable function $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\Theta, \mathcal{B}(\Theta))$$  We denote $\hat{\theta}(X) := T(X).$
>- Define the **loss function** as $$L(\theta, \hat{\theta})$$
>- Define the **risk function** as $$R(\theta, \hat{\theta}) := \mathbb{E}_{ \mathcal{P}_{\theta} }\left[ L(\theta, \hat{\theta}(X)) \right] = \int_{\Omega}\,L(\theta, \hat{\theta}(x))\,d\mathcal{P}_{\theta}(x)$$
>
>The decision problem as described above is called an **estimation** problem.
>- The decision rule $\hat{\theta}$ in point estimation problem is called an **estimator**. 

^994e95

- [[Parametric Models]]
- [[Statistical Decision Problem]]
- [[Statistics]]
- [[Point Estimator]]
- [[Mathematical Statistics by Shao]] pp 114

## Explanation



## Examples




- [[Minimum Mean Square Estimation]]





-----------
##  Recommended Notes and References



- [[Population and Sample and Statistical Problem]]

- [[All of Statistics A Concise Course by Wasserman]] pp 195
- [[Mathematical Statistics by Shao]] pp 113 - 116
- [[Statistical Decision Theory by Berger]]
