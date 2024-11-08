---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - math/functional_analysis
  - deep_learning/generative_models
  - machine_learning/kernel_methods
keywords:
  - integral_probability_metric
topics:
  - information_theory
  - information_geometry
  - machine_learning/kernel_methods
  - machine_learning_theory
  - deep_learning/generative_models
name: Integral Probability Metric between Probability Measures
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Integral Probability Metric between Probability Measures



## Explanation

### Compare with $f$-divergence and Wasserstein Distance

>[!important]
>- **Wasserstein distance** $$\mathcal{W}_{1}(\alpha, \beta) = \sup\left\{ \int_{\mathcal{X}}\phi\;d\alpha -  \int_{\mathcal{X}}\phi\;d\beta:  \;\forall \phi \in \mathcal{C}(\mathcal{X}) \text{ with } \text{Lip}(\phi) \le 1 \right\}$$
>- **$f$-divergence** $$\mathbb{D}_{f}\left( \alpha \left\|\right. \beta \right) = \sup\left\{ \int_{\mathcal{X}}\,\phi\;d\alpha - \int_{\mathcal{X}}\,f^{*}(\phi)\,d\beta:\; \forall \phi \in \mathcal{B}(\mathcal{X}) \text{ and measureable}  \right\} $$


- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]
- [[Variational Formula for f-Divergence]]
- [[f-Divergence]]



-----------
##  Recommended Notes and References



- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Principle of Learning by Comparison for Implicit Generative Models]]

- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]



- [[Statistical Manifold as Parametric Family]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[RKHS of Gaussian Process]]
- [[Gaussian Process]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 57,  889


