---
tags:
  - concept
  - math/information_theory
  - statistics/estimation
  - math/information_geometry
keywords:
  - renyi_divergence
  - renyi_entropy
topics:
  - information_geometry
  - information_theory
name: Renyi Divergence and Renyi Entropy
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
>- To distinguish with $\alpha$-divergence, we also denote it as $$\mathbb{R}_{\alpha}\left( P \left\|\right. Q \right)$$


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


### $\alpha$-divergence and $f$-divergence

![[alpha-Divergence#^bb3c1f]]

>[!important]
>**Rényi divergence** is also called **Rényi $\alpha$-divergence**. 
>
>We distinguish this with the **$\alpha$-divergence** (denoted as $\mathbb{D}^{(\alpha)}$) in Amari's book, from *$\alpha$-connection*.
>
>- There is an *one-to-one monotone mapping* between the **Rényi divergence** (LHS) and the **$\alpha$-divergence** (RHS)
>$$\mathbb{R}_{\alpha}\left( P \left\|\right. Q \right) = \frac{1}{\alpha - 1}\log \left\{1 + \alpha(\alpha - 1)\; \mathbb{D}^{(\alpha)}\left( P \left\|\right. Q \right)\right\}$$
>
>This also means that **Rényi divergence** is **not** *$f$-divergence*.

^a36567

- [[alpha-Divergence]]
- [[f-Divergence]]


## Properties

### Convexity


### Pythagorean Inequality


- [[Bregman Divergence]]

### Data Processing Inequality

>[!important] Data-processing Inequality
>Let $(\Omega, \mathscr{F})$ be a measureable space and $$\mathscr{G} \subseteq \mathscr{F}$$ be a **sub-$\sigma$-algebra**. Assume $P, Q$ are two probabilty measures on $\mathscr{F}$ with $P \ll Q$.
>
>Then the **Renyi divergence** of $P$ from $Q$ is **no less than** the **Renyi divergence**  $P$ from $Q$ **conditioned on** $\mathscr{G}$
>
>$$
>\mathbb{D}_{\alpha}\left( P \left\|\right. Q \right) \ge \mathbb{D}_{\alpha}\left( P|_{\mathscr{G}} \left\|\right. Q|_{\mathscr{G}} \right)
>$$
>for $\alpha \in [0,\infty].$

^39e8c9

- [[Data-Processing Inequality]]



-----------
##  Recommended Notes and References


- [[Mixture Embedding and Representation of Tangent Space of Statistical Manifold]]
- [[Statistical Manifold as Parametric Family]]


- [[Kullback-Leibler Divergence]]
- [[Shannon Entropy]]


- [[Elements of Information Theory by Cover]] pp 676 - 677
- Van Erven, T., & Harremos, P. (2014). Rényi divergence and Kullback-Leibler divergence. _IEEE Transactions on Information Theory_, _60_(7), 3797-3820.
- Li, Y., & Turner, R. E. (2016). Rényi divergence variational inference. _Advances in neural information processing systems_, _29_.