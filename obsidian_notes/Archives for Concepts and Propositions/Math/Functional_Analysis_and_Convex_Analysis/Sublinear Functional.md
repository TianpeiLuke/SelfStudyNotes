---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords:
  - sublinear_functional
topics:
  - functional_analysis
name: sublinear functional
date of note: 2024-05-08
---

## Concept Definitions

>[!important]
>**Name**:  Sublinear Functional

>[!important] Definition on $\mathbb{R}$
>If $X$ is a vector space, a **sublinear functional** on $X$ is a map $p: X \rightarrow \mathbb{R}$ such that 
> 
> - **Homogeneity**: $$p(\lambda x) = \lambda p(x)$$ for all $\lambda \ge 0$ and $x \in X$;
> - **Sublinearity**: $$p(x + y) \le p(x) + p(y)$$
> 

## Explanation

>[!important] Definition on $\mathbb{C}$
>If $X$ is a complex vector space, a **sublinear functional** on $X$ is a map $p: X \rightarrow \mathbb{C}$ such that 
> 
> - **Homogeneity**: $$p(\lambda x) = \lvert \lambda \rvert p(x)$$ for all $\lambda \in \mathbb{C}$ and $x \in X$;
> - **Sublinearity**: $$p(x + y) \le p(x) + p(y)$$
> 

>[!info] Equivalent form
>$$
>p(\lambda x + \mu y) \le \lvert \lambda \rvert p(x) + \lvert \mu \rvert p(y)
>$$ 
>for all $\lambda, \mu \in \mathbb{C}$ and $x, y  \in X$;



-----------
##  Recommended Notes and References

- [[Minkowski Functional]]
- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Bounded Linear Functional]]
- [[Convex Set]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)