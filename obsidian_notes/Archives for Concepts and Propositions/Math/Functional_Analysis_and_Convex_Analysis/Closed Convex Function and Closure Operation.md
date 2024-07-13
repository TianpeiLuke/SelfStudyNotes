---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - optimization/algorithm
keywords:
  - closed_convex_function
  - closure_of_convex_function
topics:
  - convex_analysis
  - optimization/theory
  - optimization/algorithm
name: Closed Convex Function and Closure Operation
date of note: 2024-07-12
---

## Concept Definition

>[!important]
>**Name**: 

>[!important] Definition
>The **closure** of a *convex function* $f$ is defined to be the *lower semi-continuous hull* of $f$ if $f$ is nowhere taking value as $-\infty.$ It is denoted as $\text{cl}(f)$.
>
>For there exists some $x$ such that $f(x) = -\infty$, then $\text{cl}(f) = -\infty.$



>[!important] Definition
>A *convex function* is said to be **closed** if and only if $$\text{cl}(f) = f.$$ That is, $f$ is its own *lower semi-continuous hull*.

- [[Convex Function]]
- [[Semi-Continuous Function]]

## Explanation



## Proper Function

>[!important] Proposition
>If $f$ is a **proper convex function**, $f$ is **closed** *if and only if* $f$ is **lower semi-continuous**.

- [[Proper Convex Function]]
- [[Semi-Continuous Function]]



-----------
##  Recommended Notes and References

- [[Epigraph or Supergraph of Function]]

- [[Convex Function]]
- [[Closed Set]]
- [[Closure of Set]]



- [[Convex Analysis by Rockafellar]] 
- [[Convex Optimization by Boyd]]. pp 52