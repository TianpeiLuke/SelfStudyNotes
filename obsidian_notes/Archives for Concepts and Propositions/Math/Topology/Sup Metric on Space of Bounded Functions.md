---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - sup_metric
topics:
  - functional_analysis
  - topology
name: sup metric on bounded functions
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  The Sup Metric on the space of Bounded Functions $\mathcal{B}(X, Y)$


>[!important] Defintion
>If $(Y, d)$ is a metric space, one can define another metric on the set $\mathcal{B}(X, Y)$ of **bounded functions** from $X$ to $Y$ by the equation
> $$
> \begin{align*}
> \rho(f, g) = \sup\set{d(f(x), g(x)): x \in X}, \quad \forall f, g \in \mathcal{B}(X, Y).
> \end{align*}
> $$
>
>It is easy to see that $\rho$ is well-defined, for the set $f(X) \cup g(X)$ is *bounded* if both $f(X)$ and $g(X)$ are. The metric $\rho$ is called **the sup metric**.

- [[Bounded Function and Space of Bounded Functions]]


## Explanation





-----------
##  Recommended Notes and References

- [[Metric Space]]
- [[Space of all Continuous Functions]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)