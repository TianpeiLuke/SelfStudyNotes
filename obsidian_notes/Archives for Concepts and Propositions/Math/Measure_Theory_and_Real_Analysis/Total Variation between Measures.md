---
tags:
  - concept
  - math/measure_theory
  - math/information_theory
  - math/probability
  - math/optimal_transport
keywords:
  - total_variation_measure
topics:
  - measure_theory
  - information_theory
  - optimal_transport
  - probability
name: Total Variation between Measures
date of note: 2024-05-23
---

## Concept Definition

>[!important]
>**Name**: Total Variation between Measures

>[!important] Definition
>Let $\mathcal{P}, \mathcal{Q}$ be two *probability measures* on measurable space $(\Omega, \mathscr{F})$. 
>
>The **total variation** or **variational distance** between $\mathcal{P}$ and $\mathcal{Q}$ is defined by
>$$
> \begin{align}
> V(\mathcal{P},\mathcal{Q}) &:= \sup_{A \in \mathscr{F}} |\mathcal{P}(A) - \mathcal{Q}(A)| 
> \end{align}
>$$ 



## Explanation

>[!important]
>It is a well-known and simple fact that the total variation is **half the $L_1$-distance**, that is, if $\mu$ is a *common dominating measure* of $\mathcal{P}$ and $\mathcal{Q}$ and $$p(x) = \frac{d\mathcal{P}}{d\mu} \quad q(x) = \frac{d\mathcal{Q}}{d\mu}$$ denote their respective *densities*, then
>$$
> \begin{align}
> V(\mathcal{P}, \mathcal{Q}) &:=  |P(A^{*}) - Q(A^{*})|  = \frac{1}{2}\int_{\Omega}|p(x) - q(x)| \;d\mu(x), 
> \end{align}
>$$  
>where $A^{*} = \set{x: p(x) \ge q(x)}$.

- [[Lp Space]]


## Total Variation as $f$-Divergence

![[f-Divergence#^3efb2b]]

- [[f-Divergence]]


## Total Variation as Integral Probability Metric



>[!important]
>The only **integral probability metric** that is also a *$f$-divergence* is the **total variation** of measure.

- [[Integral Probability Metric between Probability Measures]]



## Total Variation as Wasserstein Distance

>[!important]
>We note that another important interpretation of **the variational distance** is related to the **optimal coupling** of the two measures:
>$$
> \begin{align}
> V(\mathcal{P}, \mathcal{Q}) &= \min_{\pi \in \mathcal{M}_{+}(X \times Y)} \pi\set{X \neq Y}\\
>\text{s.t. }\;&\; X \sim \mathcal{P}\\
>&\; Y \sim \mathcal{Q}
> \end{align}
>$$  
>where the *minimum* is taken over **all pairs of joint distributions** $\mathcal{M}_{+}(X \times Y)$ for the random variables $(X, Y)$, whose marginal distributions are $X \sim P$ and $Y \sim Q$. 

- [[Space of Bounded Signed Measures]]
- [[Optimal Transport in Space of Measures]]
- [[Weighted Hamming Distance]]
- [[Wasserstein Distance]]

>[!important] 
> *The variational distance*  between $\mathcal{P}$ and $\mathcal{Q}$ is a **1-Wasserstein distance** where the induced metric is the **Hamming distance**, i.e.
> $$
> d_{H}(x, y) = \sum_{i}\mathbb{1}\left\{ x_{i} \neq y_{i} \right\}
> $$
> 
> That is, 
>$$
>\mathcal{W}_{d_{h}}(\mathcal{P}, \mathcal{Q}):= \min \left\{\pi(d_{H}(X, Y)): \pi \in \mathcal{M}_{+}(X \times Y),\; X \sim \mathcal{P}, Y \sim \mathcal{Q}  \right\} 
>$$

- [[Wasserstein Distance]]
- [[Weighted Hamming Distance]]

## Hinge Loss and Density Ratio Estimation

![[Density Ratio Estimation via Binary Classifiers#^9345f7]]

- [[Density Ratio Estimation via Binary Classifiers]]
- [[Hinge Loss as Surrogate Loss Function]]






-----------
##  Recommended Notes and References

- [[Space of Bounded Signed Measures]]
- [[Measure Space and Countably Additive Measure]]

- [[Kullback-Leibler Divergence]]


- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Probability and Measure by Billingsley]]
- [[Elements of Information Theory by Cover]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]