---
tags:
  - concept
  - math/information_theory
  - statistics/estimation
  - math/information_geometry
keywords: 
topics: 
name: 
date of note: 2024-11-03
---

## Concept Definition

>[!important]
>**Name**: Rényi Divergence and Rényi Entropy

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be *$\sigma$-finite measure space*. Let $P$ and $Q$ be *probability measures* on $(\Omega, \mathscr{F})$ that are dominated by $\mu$. 
>- Let $p(x), q(x)$ be p.d.f. of $P, Q$ with respect to $\mu$.
>- Assume that  $P$ is *absolutely continuous* with respect to $Q$,  $$P \ll Q.$$
>  
>For $\alpha \in (0,1) \cup (1, \infty)$, the **Rényi divergence** from $Q$ to $P$ is defined as 
>$$
>\begin{align*}
>\mathbb{D}_{\alpha}\left( P \left\|\right. Q \right) &=  \frac{1}{\alpha - 1} \log \int_{\mathcal{X}} \left(\frac{dP}{dQ}\right)^{\alpha}\,dQ \\[8pt]
>&=\frac{1}{\alpha - 1}\log \int_{\mathcal{X}}\,p^{\alpha}\,q^{1 - \alpha}\,d\mu
>\end{align*}
>$$
>where $dP / dQ$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Probability Density Function of Random Variable]]
- [[Radon-Nikodym Derivative]]

>[!important] Definition
>Let $p = [p_{i}], q = [q_{i}]$  be *probability mass function* for *discrete distributions* $P$ and $Q$. 
>
>Then the **Rényi divergence** from $Q$ to $P$ is defined as 
>$$
>\begin{align*}
>\mathbb{D}_{\alpha}\left( P \left\|\right. Q \right) &=  \frac{1}{\alpha - 1} \log \sum_{i=1}^{n} p_{i}^{\alpha}\,q_{i}^{1 - \alpha}
>\end{align*}
>$$
>where $\alpha \in (0,1) \cup (1, \infty)$.

### Renyi Entropy

>[!important] Definition
>Let $p = [p_{i}]$  be *probability mass function* for *discrete distributions* $P$. 
>
>Then the **Rényi entropy** of probability $P$ is defined as 
>$$
>\begin{align*}
>H_{\alpha}\left( P \right) &=  \frac{1}{\alpha - 1} \log \sum_{i=1}^{n} p_{i}^{\alpha}
>\end{align*}
>$$
>where $\alpha \in (0,1) \cup (1, \infty)$.

>[!important] Definition
>Let $p = [p_{i}]$  be *probability density function* with respect to Lebesgue measure for *continuous distribution* $P$. 
>
>Then the **differential Rényi entropy** of probability $P$ is defined as 
>$$
>\begin{align*}
>H_{\alpha}\left( P \right) &=  \frac{1}{\alpha - 1} \log \int_{\mathcal{X}} (p(x))^{\alpha}\,dx
>\end{align*}
>$$
>where $\alpha \in (0,1) \cup (1, \infty)$.



## Explanation





-----------
##  Recommended Notes and References


- [[Mixture Embedding and Representation of Tangent Space of Statistical Manifold]]
- [[Statistical Manifold as Parametric Family]]

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]
- [[alpha-Divergence]]
- [[Shannon Entropy]]


- [[Elements of Information Theory by Cover]]
- Van Erven, T., & Harremos, P. (2014). Rényi divergence and Kullback-Leibler divergence. _IEEE Transactions on Information Theory_, _60_(7), 3797-3820.