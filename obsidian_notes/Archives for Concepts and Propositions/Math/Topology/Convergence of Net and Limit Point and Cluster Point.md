---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - net_convergence
  - limit_point
  - cluster_point
topics:
  - topology
name: Convergence of Net and Limit Point and Cluster Point
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Convergence of Net and Limit Point and Cluster Point

>[!important] Definition
>A *net* $\set{x_\alpha}_{\alpha \in I}$  in a *topological space* $X$ is said to **converge** *to a point* $x \in X$, written $$x_{\alpha} \rightarrow x,$$ if for *any neighborhood* $N$ of $x$, there *exists* a $\beta \in I$ so that $x_{\alpha} \in N$ if $\alpha \succeq \beta$. 
>$$
>x_{\alpha} \rightarrow x \iff  (\forall N \ni x) \; (\exists \beta \in I)\; (\forall \alpha \succeq \beta)\;\; x_{\alpha} \in N 
>$$

>[!important] Definition
>The point $x$ that *being converged to* is called **the limit point** of  $x_{\alpha}$.

- [[Net as Generalized Sequence in Topological Space]]
- [[Directed System of Index Set]]
- [[Limit Point]]


>[!info]
> Note that if $x_\alpha \rightarrow x$, then $x_{\alpha}$ is **eventually** *in __all neighborhoods__* of $x$. 

>[!important] Definition
> If $x_{\alpha}$ is **frequently** *in __any neighborhood__ of* $x$, we say that $x$ is a **cluster point** of $x_{\alpha}$. 


## Explanation






-----------
##  Recommended Notes and References

- [[Limit Point]]
- [[Net as Generalized Sequence in Topological Space]]
- [[Directed System of Index Set]]

- [[Functional Analysis by Reed]]
- [[Topology Book by Munkres]]