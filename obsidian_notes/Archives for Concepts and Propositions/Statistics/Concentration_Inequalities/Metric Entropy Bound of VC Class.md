---
tags:
  - concept
  - statistics/concentration_inequality
  - machine_learning/theory
  - math/stochastic_process
keywords:
  - metric_entropy
  - vc_class
topics:
  - concentration_inequality
  - machine_learning_theory
  - stochastic_process
name: Metric Entropy Bound of VC Class
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Metric Entropy Bound of VC Class

>[!important] Theorem
>Let $\mathcal{F}$ be a class of **Boolean functions** on a probability space $(\mathcal{X},\mathscr{F}, \mathcal{F})$. 
>
>Then, for every $\epsilon \in (0, 1)$, we have
> $$
> \begin{align}
> \mathcal{N}(\mathcal{F}, L_2(\mathcal{P}), \epsilon) &\le \left(\frac{2}{\epsilon}\right)^{Cd}, 
> \end{align}
>$$  
>where $d =\text{VC-dim}(\mathcal{F})$ is the **VC dimension** of $\mathcal{F}$.


- [[VC Dimension]]
- [[Covering Number of Metric Space]]
- [[Metric Entropy of Metric Space]]
- [[Vapnik-Chervonenkis Class]]

## Explanation

>[!info]
>The **metric entropy bound**  for a *VC class* of boolean functions under $L^2$ norm is given by
>$$
>\log \mathcal{N}(\mathcal{F}, L_2(\mathcal{P}), \epsilon) \le\; C\,d\;\log \left(\frac{2}{\epsilon}\right)
>$$

- [[Metric Entropy of Metric Space]]
- [[Vapnik-Chervonenkis Class]]



-----------
##  Recommended Notes and References

- [[Vapnik-Chervonenkis Class]]
- [[Glivenko-Cantelli Class]]

- [[Covering Number of Metric Space]]
- [[Metric Entropy of Metric Space]]
- [[VC Dimension]]
- [[Empirical Process and Empirical Measure]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]