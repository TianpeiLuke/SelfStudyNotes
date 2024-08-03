---
tags:
  - concept
  - statistics/concentration_inequality
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - rademacher_complexity
  - convex_hull_function_class
topics:
  - machine_learning_theory
  - machine_learning_models
name: Rademacher Complexity of a Convex Hull of Function Class
date of note: 2024-07-30
---

## Concept Definition

>[!important]
>**Name**: Rademacher Complexity of a Convex Hull of Function Class

>[!important] Proposition
>Let $\mathcal{H}$ be a set of functions mapping from $\mathcal{X}$ to $\mathbb{R}$. 
>
>Then, for any sample $\mathcal{D}$, we have
>$$
> \begin{align}
> \widehat{\mathfrak{R}}_{\mathcal{D}}(\text{conv}(\mathcal{H}))  = \widehat{\mathfrak{R}}_{\mathcal{D}}(\mathcal{H}) 
> \end{align}
>$$  
>where $\text{conv}(\mathcal{H})$ is the **convex hull** of set $\mathcal{H}$
>$$
> \begin{align*}
> \text{conv}(\mathcal{H}) := \left\{\sum_{k=1}^{p}\lambda_k h_k:  p \ge 1, \forall k \in [1, p], \lambda_k \ge 0, h_k \in \mathcal{H}, \sum_{k=1}^{p}\lambda_k \le 1 \right\}.
> \end{align*}
>$$ 

^4f410b

- [[Convex Hull]]
- [[Rademacher Complexity]]




## Explanation






-----------
##  Recommended Notes and References


- [[AdaBoost Algorithm]]
- [[Generalization Error Bound for AdaBoost Finite Case]]
- [[Rademacher Complexity Bound for Binary Classification]]

- [[Rademacher Complexity]]
- [[Empirical Risk Minimization]]



- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]