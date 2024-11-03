---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - lipschitz_continuous_function
topics:
  - topology
name: Lipschitz continuous function
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Lipschitz Continuous Function


>[!info] Recall
>A map $F: X \rightarrow Y$ is said to be **continuous** if for *every open subset* $U \subseteq Y$, the *preimage* $F^{-1}(U)$ is *open* in $X$.

- [[Continuous Function]]

>[!important] Definition
>Let $(X, d_{X})$ and $(Y, d_{Y})$ be two *metric spaces*. A function $f: X \to Y$ is **Lipschitz continuous** if there exists a *constant number* $K >0$ such that for *every* two points $x, y \in X$
>$$
>d_{Y}(f(x), f(y)) \le K\, d_{X}(x, y).
>$$
>$f$ is also called **$K$-Lipschitz.**

>[!important] Definition
>A constant number $K >0$ satisfies above condition is called a **Lipschitz constant**.
>
>The **smallest** Lipschitz constant is called **the (best) Lipschitz constant** of $f$ or the **dilation** or **dilatation**.



## Explanation

>[!important]
>*Lipschitz continuity* is a **strong form** of **uniform continuity** for functions.

- [[Uniform Topology on Metric Spaces]]

>[!important]
>*Lipschitz continuity* means that the function has **contraction property**. That is, the distance between points **shrinks** after each mapping.

- [[Contraction Function]]

>[!important]
>The power of Lipschitz function lies its ability to push *metric topology* from the **domain** and **codomain**.
>
>A neighborhood in domain will map to a neighborhood in codomain.


## Relationship with Other Continuity


>[!important]
>**Continuously differentiable** $\subset$ **Lipschitz continuous** $\subset$ **absolutely continuous**  $\subset$ **uniformly continuous**

- [[Space of Continuous Differentiable Functions]]
- [[Uniform Topology on Metric Spaces]]

## Differentiation Theorem

- [[Lipschitz and Rademacher Differentiation Theorem]]

## Second Fundamental Theorem of Calculus

- [[Second Fundamental Theorem of Calculus Lipschitz]]

## Variational Representation of Wasserstein Distance

- [[Wasserstein Distance]]
- [[Variational Representation of Wasserstein Distance]]

## Concentration of Measure

- [[Lévy Inequalities]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Concentration of Separately Convex Lipschitz Functions]]
- [[Concentration of Lipschitz Function of Gaussian Vector]]
- [[Concentration of Quasi-Convex Lipschitz Functions]]
- [[Transportation Cost Inequality in Hamming Metric Space]]
- [[Talagrand Gaussian Transportation Inequality]]




-----------
##  Recommended Notes and References

- [[Hölder Condition and Hölder Continuous Function]]

- [[Metric Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)