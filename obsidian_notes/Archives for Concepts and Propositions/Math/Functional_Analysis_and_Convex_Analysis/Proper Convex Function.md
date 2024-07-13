---
tags:
  - concept
  - math/convex_analysis
  - optimization/algorithm
  - optimization/theory
keywords:
  - proper_function
  - proper_convex_function
topics:
  - convex_analysis
  - optimization/theory
  - optimization/algorithm
name: Proper Convex Function
date of note: 2024-07-12
---

## Concept Definition

>[!important]
>**Name**: Proper Convex Function

>[!important] Definition
>A *convex function* $f: \mathcal{X} \to \mathbb{R}$ is said to be **proper** if its *epigraph*
>$$
>\text{epi}(f) = \{ (x, \mu) \in \mathcal{X}\times \mathbb{R}:  f(x) \le \mu\} \neq \emptyset
>$$
>is non-empty and does not contain *vertical line*.
>
>That is, 
>- there exists *at least one* $x\in \mathcal{X}$ such that $$f(x) < +\infty$$
>- and, *for all* $x\in \mathcal{X}$ such that $$f(x) > -\infty.$$

- [[Epigraph or Supergraph of Function]]

## Explanation

>[!info]
>Equivalently, $f$ is **proper** if and only if
>- the *effective domain* is non-empty $$C := \text{dom}(f) \neq \emptyset$$
>- the *restriction* of $f$ on its effective domain is *finite* $$f\big|_{C}: C \to (-\infty, +\infty)$$
>  
>That is, $f$ is proper if and only if it is an extension of $f|_{C}$ where  
>$$
>f(x) =  f\big|_{C}(x) + \delta(x\,|\,C) := \left\{\begin{array}{cc}
> f\big|_{C}(x) & x \in C\\
> +\infty & x \not\in C
>\end{array}
>\right. 
>$$  




-----------
##  Recommended Notes and References

- [[Epigraph or Supergraph of Function]]
- [[Semi-Continuous Function]]
- [[Convex Function]]
- [[Closed Set]]
- [[Closed Map]]


- [[Convex Analysis by Rockafellar]] pp 24
- [[Convex Optimization by Boyd]] 