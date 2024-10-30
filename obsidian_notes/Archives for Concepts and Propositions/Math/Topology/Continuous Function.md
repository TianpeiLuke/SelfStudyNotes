---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - continuous_function
topics:
  - topology
name: continuous function
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Continuous Function


>[!important] Definition
>A map $F: X \rightarrow Y$ is said to be **continuous** if for *every open subset* $U \subseteq Y$, the *preimage* $F^{-1}(U)$ is *open* in $X$.

- [[Preimage and Range of Function]]
- [[Topology of Set]]

>[!important] Definition
>The space of all **continuous functions** from X to Y is denoted as $\mathcal{C}(X, Y)$
> $$
> \mathcal{C}(X, Y) = \left\{ f: X \rightarrow Y:  f^{-1}(U) \in \mathscr{T}_{X}, \text{ for every }U\in \mathscr{T}_{Y} \right\}
> $$



## Explanation

>[!important]
>**Continuouity** is a basic property of function that is compatible with the notion of **topology**. 
>
>Given the topology on **domain** and **co-domain**, we can always define a continuous function. 

## Continuous Functional in Metric Space and Normed Linear Space

>[!important] Definition
>Let $(X, d_{X})$  and $(Y, d_{Y})$ be *metrix spaces.*
>
>A functional $$f: X \to Y$$ is **continuous** at $x_{0}\in X$ if for any $\epsilon >0$, there exists some $\delta >0$ such that 
>$$
>d_{X}(x, x_{0}) < \delta \implies d_{Y}(f(x), f(x_{0})) < \epsilon  
>$$

- [[Metric Space]]

>[!important] Definition
>Let $(X, \lVert \cdot \rVert_{X})$ be a *normed linear space*. 
>
>A functional $$f: X \to \mathbb{R}$$ is **continuous** at $x_{0}\in X$ if for any $\epsilon >0$, there exists some $\delta >0$ such that 
>$$
>\lVert x - x_{0} \rVert_{X} < \delta \implies \lvert f(x) - f(x_{0}) \rvert < \epsilon  
>$$

- [[Norm and Normed Space]]




-----------
##  Recommended Notes and References

- [[Topology of Set]]
- [[Function]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)