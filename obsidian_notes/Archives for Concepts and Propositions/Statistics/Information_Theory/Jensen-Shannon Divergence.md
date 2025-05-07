---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
keywords:
  - jensen_shannon_divergence
topics:
  - information_theory
  - information_geometry
name: Jensen-Shannon Divergence
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Jensen-Shannon Divergence

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a meaureable space, and $P, Q$ are two probability measures on $\mathscr{F}$.
>
>The **Jensen-Shanon divergence (JSD)** between $P$ and $Q$ is defined as 
>$$
>\mathbb{D}_{JSD}\left( P \left\|\right. Q \right) := \frac{1}{2}\mathbb{KL}\left( P \left\|\right. M \right) + \frac{1}{2}\mathbb{KL}\left( Q \left\|\right. M \right)
>$$ 
>where $M$ is defined as the *mixture model* between $P$ and $Q$ $$M = \frac{1}{2}P + \frac{1}{2}Q$$
>- Note that $P \ll M, \quad Q\ll M.$
>- The **Jensen-Shanon divergence (JSD)** is *symmetrized* and *smoothed version* of *KL-divergence* $$\mathbb{D}_{JSD}\left( P \left\|\right. Q \right) = \mathbb{D}_{JSD}\left( Q \left\|\right. P \right)$$

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Mixture Family of Distributions]]
- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Gaussian Mixture Models or GMM]]

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a meaureable space, and $P_{1}\,{,}\ldots{,}\,P_{K}$ are probability measures on $\mathscr{F}$.
>
>The **Jensen-Shanon divergence (JSD)** for $P_{1}\,{,}\ldots{,}\,P_{K}$  is defined as 
>$$
>\begin{align*}
>\mathbb{D}_{JSD}\left( P_{1}\,{,}\ldots{,}\,P_{K} \right) &:= \sum_{i=1}^{K}\pi^{i}\,\mathbb{KL}\left( P_{i} \left\|\right. M \right) \\[5pt]
>&= H(M) - \sum_{i=1}^{K}\pi^{i}\,H(P_{i})
>\end{align*}
>$$ 
>where
>- $$(\pi^{1}\,{,}\ldots{,}\,\pi^{K}) \in \Delta_{K} := \left\{ (p^{1}\,{,}\ldots{,}\,p^{K}) \in [0,1]^{K}\,:\, \sum_{i=1}^{K}p_{i} = 1 \right\} $$
>- and $M$ is defined as the *mixture model* with components $P_{1}\,{,}\ldots{,}\,P_{K}$, i.e. $$M = \sum_{i=1}^{K}\pi^{i}\,P_{i}$$
>- Note that $P_{i} \ll M.$
>- The **Jensen-Shanon divergence (JSD)** is seen as the total divergence for a cluster of distributions to its *barycenter* in *statistical manifold* under the **mixture connection.**

- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Mixture Family of Distributions]]



## Explanation

>[!important]
>The **Jensen-Shanon divergence (JSD)** is the **mutual information** between $X$ and $Z$ where
>- the random variable $X$ follows the mixture distribution $$X \sim M = \frac{P + Q}{2}$$
>- and the random variable $Z$ is defined as the *binary indicator* for *switching* between $P$ and $Q$ $$X \sim \left\{\begin{array}{cl} P & \text{ if }Z = 0 \\[5pt] Q &  \text{ if }Z = 1\end{array}\right.$$
>
>Thus 
>$$
>\begin{align*}
> I(X; Z) &= H(X) - H(X|Z) \\[5pt]
> &= - \int M \log(M) + \frac{1}{2} \left\{ \int P \log(P) + \int Q \log(Q) \right\}  \\[5pt]
> &= - \frac{1}{2} \int P \log(M) - \frac{1}{2} \int Q \log(M) + \frac{1}{2} \left\{ \int P \log(P) + \int Q \log(Q) \right\}  \\[5pt]
> & = \frac{1}{2} \int P \left( \log(P) - \log(M) \right) + \frac{1}{2} \int Q \left( \log(Q) - \log(M) \right)\\[5pt]
> &:= \mathbb{D}_{JSD}\left( P \left\|\right. Q \right)
>\end{align*}
>$$

- [[Mutual Information]]

## Property

>[!important] Propostion
>Let $(\Omega, \mathscr{F})$ be a meaureable space, and $P, Q$ are two probability measures on $\mathscr{F}$.
>
>The **Jensen-Shanon divergence (JSD)** between $P$ and $Q$ is bounded between $[0,\log(2)]$ 
>$$
> 0 \le \mathbb{D}_{JSD}\left( P \left\|\right. Q \right) \le \log(2)
>$$ 
>- If $P_{1}\,{,}\ldots{,}\,P_{K}$ are probability measures on $\mathscr{F}$, then  
>$$
> 0 \le \mathbb{D}_{JSD}\left( P_{1}\,{,}\ldots{,}\,P_{K} \right) \le \log (K)
>$$ 


>[!important] Propostion
>Let $(\Omega, \mathscr{F})$ be a meaureable space, and $P, Q$ are two probability measures on $\mathscr{F}$.
>
>The **Jensen-Shanon divergence (JSD)** between $P$ and $Q$ is *bounded above* by the **total variations**
>$$
> \mathbb{D}_{JSD}\left( P \left\|\right. Q \right) \le \frac{1}{2} V(P, Q) := \frac{1}{2}\sup_{A \in \mathscr{F}} |P(A) - Q(A)| 
>$$ 

- [[Total Variation between Measures]]


## Centroid 

>[!important] Definition
>Let $p_{1}\,{,}\ldots{,}\,p_{K}$ be $K$ p.d.f.s in a statistical manifold $\mathcal{S}$.
>
>The **centroid** $C$ of  $p_{1}\,{,}\ldots{,}\,p_{K}$ is given by *moment-projection*
>$$
>C^{*} = \arg\min_{C} \frac{1}{K}\sum_{i=1}^{K}\mathbb{KL}\left( p_{i} \left\|\right.  C\right)
>$$
>which is the **mixture** of $p_{1}\,{,}\ldots{,}\,p_{K}$, i.e. $$C^{*} := \frac{1}{K}\sum_{i=1}^{K}p_{i} \in \mathcal{S}$$
>and the corresponding *minimum total divergence* is the **Jensen-Shanon divergence (JSD)** $$\mathbb{D}_{JSD}\left( P_{1}\,{,}\ldots{,}\,P_{K} \right) = \min \frac{1}{K}\sum_{i=1}^{K}\mathbb{KL}\left( p_{i} \left\|\right.  C\right)$$

- [[Information Projection and Moment Projection]]

## Convex-Concave Procedure

- [[Difference of Convex Optimization and Concave-Convex Procedure]]

## f-Divergence

>[!info]
>The *Jenson-Shannon divergence* is a $f$-divergence.

![[f-Divergence#^a66a56]]

- [[f-Divergence]]

## Density Ratio Estimation

![[Density Ratio Estimation via Binary Classifiers#^e7d9e0]]

- [[Density Ratio Estimation via Binary Classifiers]]
- [[Logistic Regression]]





-----------
##  Recommended Notes and References



- [[Renyi Divergence and Renyi Entropy]]
- [[alpha-Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]

- [[Jensen Inequality]]
- [[Shannon Entropy]]

- [[Statistical Manifold as Parametric Family]]
- Wikipedia [Jensen-Shannon_divergence](https://en.wikipedia.org/wiki/Jensen%E2%80%93Shannon_divergence)

