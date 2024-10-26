---
tags:
  - concept
  - math/information_theory
  - math/functional_analysis
  - math/measure_theory
  - math/probability
  - math/optimal_transport
keywords:
  - pinsker_inequality
topics:
  - information_theory
  - optimal_transport
  - measure_theory
  - probability
name: Pinsker Inequality
date of note: 2024-05-23
---

## Concept Definition

>[!important]
>**Name**: Pinsker's Inequality

>[!important] Pinsker's Inequality
>Let $\mathcal{P}, \mathcal{Q}$ be two *probability measures* on measurable space $(\Omega, \mathscr{F})$ such that $P \ll Q.$ 
>
>Then
>$$
> \begin{align}
> V(\mathcal{P}, \mathcal{Q})^2 &\le \frac{1}{2}\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{Q} \right).
> \end{align}
>$$ 

^c30a68


- [[Total Variation between Measures]]
- [[Kullback-Leibler Divergence]]

## Explanation



## Corollary to Transportation Cost Inequality

- [[Transportation Cost Inequality]]

>[!important]
>This inequality is a corollary of the [[Transportation Cost Inequality]] for **sub-Gaussian random variables**.
>$$
> \begin{align}
> \mathbb{E}_{\mathcal{P}}\left[X\right] - \mathbb{E}_{\mathcal{Q}}\left[X\right] &\le \sqrt{2\nu \mathbb{KL}\left( \mathcal{P} \left\|\right.  \mathcal{Q} \right)  }. 
> \end{align}
>$$ 

- [[Sub-Gaussian Random Variable]]

>[!info]
>Suppose $A^{*} \in \mathscr{F}$ is the optimal subset in $\mathscr{F}$ that achieve the maximum distance. Define a random variable
>$$
>Z := \mathbb{1}\left\{ A^{*} \right\}
>$$
>$Z$ is bounded random variable, so it is [[Sub-Gaussian Random Variable]]. 
>
>By Hoeffding's Lemma, 
>$$
>\psi_{Z -  \mathbb{E}\left[ Z \right]}(\lambda) \le \frac{\lambda^2}{8}
>$$
>Thus $\nu = \frac{1}{4}.$

- [[Hoeffding Inequality]]

>[!info]
>Note that by [[Variational Representation of Wasserstein Distance]]
>$$
>V(\mathcal{P}, \mathcal{Q}) = \mathcal{W}_{d_{H}}(\mathcal{P}, \mathcal{Q}) = \sup_{\text{Lip}_{1}(X) \le 1}\left\{ \mathbb{E}_{\mathcal{P}}\left[X\right] - \mathbb{E}_{\mathcal{Q}}\left[X\right] \right\}  
>$$
>where $X$ is **Lipschitz function** with respect to **Hamming distance** and
>$$
>\text{Lip}_{1}(X):= \min\left\{ K >0: d_{H}(X(\omega_{1}), X(\omega_{2})) \le K\,d_{H}(\omega_{1}, \omega_{2}) \right\}
>$$

- [[Weighted Hamming Distance]]

>[!info]
>So by [[Transportation Cost Inequality]], 
>$$
>\begin{align*}
>\mathcal{W}_{d}(\mathcal{P}, \mathcal{Q}) = \sup_{\text{Lip}_{1}(X) \le 1}\left\{ \mathbb{E}_{\mathcal{P}}\left[X\right] - \mathbb{E}_{\mathcal{Q}}\left[X\right] \right\}  &\le \sqrt{2\nu \mathbb{KL}\left( \mathcal{P} \left\|\right.  \mathcal{Q} \right)  }\\
>&= \sqrt{\frac{1}{2}  \mathbb{KL}\left( \mathcal{P} \left\|\right.  \mathcal{Q} \right)  }
\end{align*}
>$$




-----------
##  Recommended Notes and References

- [[Total Variation between Measures]]
- [[Kullback-Leibler Divergence]]
- [[Transportation Cost Inequality]]


- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]]
- [[Elements of Information Theory by Cover]]

- [[Concentration Inequalities by Boucheron]]