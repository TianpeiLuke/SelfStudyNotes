---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - likelihood_function
topics:
  - statistics
  - statistics/estimation
name: Likelihood Function
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Likelihood Function

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *$\sigma$-finite measure space*.  
>
>Denote $\mathcal{F}_{\Theta}$ as a *parametric family* of *probability density functions (p.d.f.)* with respect to a *common dominating measure* $\mu$, i.e.,
>$$
>\mathcal{F}_{\Theta} := \left\{ f_{\theta} := \frac{d\mathcal{P}_{\theta}}{d\mu} \in L^1(\mathcal{X}, \mu): \theta \in \Theta \subset \mathbb{R}^{d} \right\}. 
>$$
>
>For each $x\in \mathcal{X}$, $f_{\theta}(x) \in \mathcal{F}_{\Theta}$ considered as a function of $\theta$ is called the **likelihood function** *of* $\theta$, denoted as $\ell(\theta; x)$,  i.e., $$\ell(\cdot; x): \theta \to f_{\theta}(x).$$

^f6d78c

- [[Probability Density Function of Random Variable]]
- [[Measure Space and Countably Additive Measure]]
- [[Probability Space]]
- [[Finite and sigma-Finite Measure]]

## Explanation

>[!important]
>The likelihood function is a **function of parameters**, instead of a **random variable**, as we need to **fixed the sample point** $x\in \mathcal{X}$.

>[!important]
>Likelihoods are *comparable*, e.g. for parameter estimation, *only if* they are *Radon–Nikodym derivatives* with respect to **the same dominating measure**.

>[!important]
>The likelihood function does **not** specify the probability that $\theta$ is the **truth**, given the observed sample $X=x$. 
>
>Such an interpretation is a **common error**, with potentially disastrous consequences
>
>Instead, the likelihood is the **probability** that **a particular outcome $x$ is observed** *under the hypothesis* that the *true* value of the parameter is $\theta.$




-----------
##  Recommended Notes and References

- [[Fundamental Lemma of Neyman and Pearson.]]

- [[Point Estimator]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Radon-Nikodym Derivative]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 274
