---
tags:
  - concept
  - deep_learning/generative_models
  - deep_learning/contrastive_learning
keywords: []
topics:
  - machine_learning_theory
  - deep_learning/generative_models
  - representation_learning
  - deep_learning/contrastive_learning
name: Density Ratio Estimation via Binary Classifiers
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Density Ratio Estimation via Binary Classifiers

>[!important]
>Let $P, Q$ be two *probability density functions* on $(\mathcal{X}, \mathscr{F},\mu)$. The task is to measure the difference between them via **ratio of density.**
>
>Consider a *binary classification problem*, where 
>- $(X,Y) \sim p$ follows a joint distribution 
>- and the conditional distribution $$P(x) := p(x|Y=1), \quad Q(x):= p(x|Y=0)$$
>
>Then the *ratio of density* is given by the *log-odds* of a binary classifier $h$ as
>$$
>\begin{align*}
>r(x) := \frac{P(x)}{Q(x)} &:= \frac{p(x|Y=1)}{p(x|Y=0)} \\[5pt]
>&=  \frac{p(Y=1|x)\,p(x)}{p(Y=1)}  / \frac{p(Y=0|x)\,p(x)}{p(Y=0)}\\[5pt]
>&= \frac{p(Y=1|x)}{p(Y=0|x)}\; \frac{1 - \pi}{\pi}\\[5pt]
>&:= \frac{h(x)}{1- h(x)}\; \frac{1 - \pi}{\pi}
>\end{align*}
>$$
>where 
>-  $\pi$ denote the **prior** on label $1$  $$\pi := p(Y=1),$$ 
>- $h$ is the *probabilistic output* of a *binary classifier* $$h(x) := p(Y=1|x)$$ 
>
>This is called the **density ratio estimation (DRE) trick**. 
>- Note that the *marginal data distribution* $p(x)$ is *cancelled* in the ratio.

^010141

- [[Bayes Theorem]]

- [[Bayes Error and Bayes Classifier]]
- [[Logistic Regression]]

### Optimize Classifier 




## Explanation

### Connection to $f$-Divergence

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]

- [[Total Variation between Measures]]
- [[Hinge Loss as Surrogate Loss Function]]

- [[Hellinger Distance between Distributions]]
- [[Exponential Loss Minimization for AdaBoost]]

- [[Chi-squared Divergence]]
- [[Logistic Regression]]

### Connection with Integral Probability Metric

- [[Integral Probability Metric between Probability Measures]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]


## Application in Contrastive Learning

- [[Noise Contrastive Estimation]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]





-----------
##  Recommended Notes and References


- [[Principle of Learning by Comparison for Implicit Generative Models]]


- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family of Distributions]]
- [[Gibbs Distribution]]
- [[Gibbs Measure and Energy-based Model]]
- [[Classification Problem]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 61 - 62


