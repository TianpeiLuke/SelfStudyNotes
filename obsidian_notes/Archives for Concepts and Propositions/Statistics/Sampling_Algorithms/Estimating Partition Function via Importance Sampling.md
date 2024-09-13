---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - statistics/estimation
  - machine_learning/theory
  - deep_learning/algorithms
keywords: 
topics: 
name: Estimating Partition Function via Importance Sampling
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Estimating Partition Function via Importance Sampling

>[!important] 
>Let $X \in \mathcal{X}$ be a random variable with p.d.f. $$p(x) = \frac{\tilde{p}(x)}{Z_{p}}$$ where $Z_{p}$ is the *partition function* and $\tilde{p}(x)$ is the unnormalized density. 
>
>We wish to use an **important sampling distribution** $$q(x) = \frac{\tilde{q}(x)}{Z_{q}}$$ to estimate the *expectation* 
>$$
>\mathbb{E}_{ p }\left[  f(X) \right] = \int_{\mathcal{X}} f(x)\,p(x)\,dx.
>$$
>
>In particular, we have
>$$
>\begin{align*}
>\mathbb{E}_{ p }\left[  f(X) \right] &= \int_{\mathcal{X}} f(x)\,p(x)\,dx \\[5pt]
>&= \int_{\mathcal{X}} f(x)\,\frac{p(x)}{q(x)}\,q(x)\,dx \\[5pt]
>&= \frac{Z_{q}}{Z_{p}} \int_{\mathcal{X}} f(x)\,\frac{\tilde{p}(x)}{\tilde{q}(x)}\,q(x)\,dx \\[5pt]
>&:= \frac{Z_{q}}{Z_{p}} \int_{\mathcal{X}} f(x)\,w(x)\,q(x)\,dx 
>\end{align*}
>$$
>where the **importance weight** is defined as
>$$
>w(x) = \frac{\tilde{p}(x)}{\tilde{q}(x)}.
>$$
>
>Now let $f\equiv 1$, we have
>$$
>1 = \mathbb{E}_{ p }\left[  f(X) \right] = \frac{Z_{q}}{Z_{p}} \int_{\mathcal{X}} \,w(x)\,q(x)\,dx 
>$$
>Hence, the **ratio of partition function** can be computed as
>$$
>\frac{Z_{p}}{Z_{q}} = \int_{\mathcal{X}} \,w(x)\,q(x)\,dx 
>$$

- [[Importance Sampling]]
- [[Probability Density Function of Random Variable]]

>[!important] Definition
>The **Importance Sampling Algorithm** to estimate the **ratio of partition function** is described as below:
>- Draw $$X_1, \ldots, X_{m} \sim q(x) = \frac{\tilde{q}(x)}{Z_{q}}$$ where $q$ is **trial p.d.f.**;
>- Calculate **the importance weight** $w(x)$:
>$$
> \begin{align*}
> w_i := w(X_i) &= \frac{\tilde{p}(X_i)}{\tilde{q}(X_i)}, \quad i=1,\ldots, m
> \end{align*}
>$$ 
>- **Approximate** $$\frac{Z_{p}}{Z_{q}}$$ by the *sum of importance weights* $$\frac{Z_{p}}{Z_{q}} \approx \frac{1}{m}\sum_{i=1}^{m} w_{i}$$ 

### Annealed Importance Sampling to Approximate Partition Function









## Explanation





-----------
##  Recommended Notes and References


- [[Annealed Importance Sampling]]
- [[Importance Sampling]]
- [[Sequential Importance Sampling]]


- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Partition Function for AdaBoost]]
- [[Gibbs Measure and Energy-based Model]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 437 - 439
- [[Deep Learning by Goodfellow]] pp 614 - 616