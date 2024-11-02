---
tags:
  - concept
  - optimization/theory
keywords:
  - unconstrained_optimization
topics:
  - optimization
name: Unconstrained Local Minimization
date of note: 2024-06-28
---
 
## Concept Definition

>[!important]
>**Name**: Unconstrained Local Minimization

>[!important] Definition
>A vector $x^{*}$ is an **unconstrained local minimum** of $f$ it is no worse than its neighbors; that is, if there exists an $\epsilon >0$ such that
>$$
>f(x^{*}) \le f(x), \quad \forall x \in B_{\epsilon}(x^{*})
>$$
>where $B_{\epsilon}(x^{*})$ is the *$\epsilon$-neighborhood* in metric space. 
>
>The *unconstrained local minimum* is said to be **strict** if 
>$$
>f(x^{*}) < f(x), \quad \forall x  \in B_{\epsilon}(x^{*}) \setminus \{  x^{*}  \} 
>$$

- [[Metric Topology and epsilon-ball]]

## Explanation


## Stationary and Singular Point 

- [[Stationary Point and Singular Point of Smooth Function]]

## Necessary and Sufficient Condition for Local Minimum of Smooth Function

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

## Functional Extension

- [[Extremum and Weak and Relative Extremum of Functional]]



-----------
##  Recommended Notes and References

- [[Unconstrained Global Minimization]]
- [[Stationary Point and Singular Point of Smooth Function]]

- [[Nonlinear Programming by Bertsekas]] pp 4
- [[Numerical Optimization by Nocedal]] pp 12