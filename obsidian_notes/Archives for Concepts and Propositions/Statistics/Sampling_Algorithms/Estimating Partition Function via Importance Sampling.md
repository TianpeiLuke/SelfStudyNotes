---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - statistics/estimation
  - machine_learning/theory
  - deep_learning/algorithms
keywords:
  - partition_function
  - importance_sampling
  - annealed_importance_sampling
topics:
  - monte_carlo
  - statistics/monte_carlo
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

![[Annealed Importance Sampling#^9aace9]]

- [[Annealed Importance Sampling]]

## Explanation

>[!quote]
>We have focused our presentation here on the problem of generating samples from a distribution so as to estimate the posterior. However, another task of significant practical importance is that of **computing the partition function** of an **unnormalized measure**. As we will see, this task is of particular importance in learning, since the normalizing constant is often used as a **measure of the overall quality** of a learned model. Computation of a partition function by directly sampling the distribution leads to estimates of *high variance*, since such estimates are usually dominated by a small number of samples with high unnormalized probabilities. In order to avoid this problem, a ratio of partition functions is computed; see exercise 12.8. An equivalent problem of **free energy difference**, or **partition function ratio**, has been tackled in computational physics and computation chemistry communities with a range of methods, including **free energy perturbation**, **thermodynamic integration**, **bridge sampling**, **umbrella sampling**, and Jarzynski equation; these methods are in essence *importance-sampling algorithms*.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 543 - 544

>[!quote]
>In situations where $\mathbb{KL}\left( p_{0} \left\|\right. p_{1} \right)$ is large (i.e., where there is *little overlap* between $p_0$ and $p_{1}$), a strategy called **annealed importance sampling (AIS)** attempts to bridge the gap by introducing *intermediate distributions* (Jarzynski, 1997; Neal, 2001).
>
>This approach enables us to estimate the partition function of a multimodal distribution defined over a *high-dimensional space* (such as the distribution defined by a trained RBM). We begin with a **simpler** model with a **known partition function** (such as an RBM with zeros for weights) and estimate the **ratio between the two model’s partition functions**. The estimate of this ratio is based on the estimate of the ratios of a sequence of many similar distributions, such as the sequence of RBMs with weights interpolating between zero and the learned weights.
>
>-- [[Deep Learning by Goodfellow]] pp 617







-----------
##  Recommended Notes and References


- [[Annealed Importance Sampling]]
- [[Importance Sampling]]
- [[Sequential Importance Sampling]]
- [[Markov Chain Monte Carlo Methods]]


- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Partition Function for AdaBoost]]
- [[Gibbs Measure and Energy-based Model]]
- [[Probabilistic Graphical Models]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 437 - 439
- [[Deep Learning by Goodfellow]] pp 614 - 616
- [[Probabilistic Graphical Models by Koller]] pp 543 - 544