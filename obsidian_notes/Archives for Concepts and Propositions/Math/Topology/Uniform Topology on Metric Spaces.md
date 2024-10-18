---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - uniform_topology_metric
topics:
  - functional_analysis
  - topology
name: uniform topology on metric spaces
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  *Uniform Metric* and *Uniform Topology* on Infinite dimensional Metric Spaces

>[!important] Definition
>Given an index set $J$, and given points $x = (x_{\alpha})_{\alpha \in J}$ and $y = (y_{\alpha})_{\alpha \in J}$ of $\mathbb{R}^{J}$,  define a metric $\bar{\rho}$ on $\mathbb{R}^{J}$ by the equation
>$$
> \begin{align*}
> \bar{\rho}(x, y) &= \sup\set{\bar{d}(x_{\alpha}, y_{\alpha}): \alpha \in J},
> \end{align*}
>$$ 
>where $\bar{d}$ is *the standard bounded metric* on $\mathbb{R}$. 
>
>It is easy to check that $\bar{\rho}$ is indeed a metric; it is called **the uniform metric** on $\mathbb{R}^{J}$,.
>
 >The *topology* $\bar{\rho}$ induces is called **the uniform topology.**

- [[Metric Space]]
- [[Standard Bounded Metric]]
- [[Metric Topology and epsilon-ball]]



## Explanation

>[!important]
>It is important to know that $J$ need not to be a finite set, i.e. $\mathbb{R}^J$ need *not to be finite dimensional.* 

>[!important]
>For infinite dimensional space,  it is important to use **standard bounded metric** $\bar{d}$ induced by $d$, instead of $d$ itself to define **the uniform metric** $\bar{\rho}$.

>[!important]
>**Uniform convergence** is the convergence with respect to **uniform topology**.

- [[Uniform Convergence]]

## Topology of Uniform Convergence in Function Space


>[!important] Uniform Topology on Function Space.
>Consider the space of functions $Y^X:= \{ f: X \to Y \}$ where $Y$ is a *metric space* with metric *$d$*. Define **the uniform metric** on $Y^X$ as 
> $$
> \begin{align*}
> \bar{\rho}(f, g) &:= \sup\{ \bar{d}(f(x), g(x)): x\in X \} 
> \end{align*}
> $$
>where $\bar{d}$ is the standard bounded metric induced by $d$. 
>
>The metric topology induced by $\bar{\rho}$ is called **the uniform topology** (or, the **topology of uniform convergence**) on $Y^X$.




-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Metric Space]]
- [[Upper Bound and Supremum of Set]]

- [[Topology Book by Munkres]]
- [[Principles of Mathematical Analysis by Rudin]] pp 147
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)