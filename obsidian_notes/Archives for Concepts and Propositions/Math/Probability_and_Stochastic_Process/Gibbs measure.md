---
tags:
  - concept
  - math/information_theory
  - math/probability
  - machine_learning/models
  - math/information_geometry
keywords:
  - gibbs_measure
topics:
  - probability
  - information_theory
  - information_geometry
  - machine_learning_models
name: Gibbs measure
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Gibbs measure

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable space. A probability measure $P$ on $\mathscr{F}$ is called **a Gibbs measure** if its density with respect to a base measure $\mu$ is of the form
>$$
>\begin{align*}
>dP(x) = \frac{1}{Z}\exp \left(- \frac{E(x)}{T}  \right)\; d\mu(x)
\end{align*}
>$$
>where $T >0$ is the **temperature** and $E(x)$ is called the **energy** of the system. 
>
>The *normalization factor* $$Z = \int_{\Omega} \exp \left(- \frac{ E(x)}{T}  \right)\; d\mu(x)$$ is called **the partition function**.

^bfb840






## Explanation

>[!important]
>Gibbs measure is the **optimal solution** for **the maximum entropy optimization**.
>$$
>\begin{align*}
>\inf_{P \ll Q} \;&\mathbb{KL}\left( P \left\|\right. Q \right)\\
>\text{s.t. }& \mathbb{E}_{P}\left[ f \right] = const.
\end{align*}
>$$
>where $f(x) := - E(x) / T.$

- [[Maximum Entropy Learning]]
- See proof in [[Variational Formula for Kullback-Leibler Divergence]]


-----------
##  Recommended Notes and References

- [[Gibbs Distribution]]
- [[Stimulated Annealing]]
- [[Restricted Boltzmann Machine]]

- [[Gaussian Random Vector]]
- [[Gaussian Measure]]

- Wikipedia [Gibbs measure](https://en.wikipedia.org/wiki/Gibbs_measure)