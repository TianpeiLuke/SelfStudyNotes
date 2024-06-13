---
tags:
  - concept
  - math/topology
  - math/functional_analysis
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - epsilon_separated
topics:
  - topology
  - functional_analysis
  - stochastic_process
  - concentration_inequality
name: epsilon-Separated Set
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: epsilon-Separated Set in Metric Space

>[!important] Definition
>Let $(T, d)$ be a *metric space* and  $K \subset T$ is a subset of $T$. Let $\epsilon > 0$.  
>
>The subset $\mathcal{N} \subset K$  is **$\epsilon$-separated** if for any $x, y \in \mathcal{N}$
>$$
> \begin{align*}
> d(x, y) > \epsilon.
> \end{align*}
>$$ 

^252e03

- [[Metric Space]]
- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Indexed Family of Sets]]

## Explanation



>[!important]
>Consider the collection of $\epsilon / 2$-balls, $$\mathscr{B} := \left\{  B\left( x, \frac{\epsilon}{2} \right), x\in \mathcal{N}  \right\},$$ we know that
>$$
> \bigcup_{x\in \mathcal{N}}B\left( x, \frac{\epsilon}{2} \right) \subset K.
>$$ 

- [[Packing Number of Metric Space]]

## Properties

>[!important] Lemma
>Let $\mathcal{N}$ be a **maximal $\epsilon$-separated** subset of $K$, that is, adding more points in $\mathcal{N}$ will *violate* the $\epsilon$-separation property. 
>
>Then $\mathcal{N}$ is an **$\epsilon$-net** of $K$.

^08741a

- [[epsilon-Cover and epsilon-Net of Metric Space]]

>[!info] Proof
>Let $x \in K$; we want to show that there exists $x_0 \in \mathcal{N}$ such that $d(x, x_0) \le \epsilon$.
> 
> - If $x \in \mathcal{N}$, the conclusion is *trivial* by choosing $x_0 = x$. 
> 
>-  Suppose now $x \not\in \mathcal{N}$. The **maximality assumption** implies that  $\mathcal{N} \cup \set{x}$ is *not $\epsilon$-separated.* But this means precisely that
>$$
> \begin{align*}
> d(x, x_0) \le \epsilon \text{ for some }x_0 \in \mathcal{N}. 
> \end{align*}
>$$ 
> Q.E.D.




-----------
##  Recommended Notes and References

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Metric Space]]


- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Topology Book by Munkres]]