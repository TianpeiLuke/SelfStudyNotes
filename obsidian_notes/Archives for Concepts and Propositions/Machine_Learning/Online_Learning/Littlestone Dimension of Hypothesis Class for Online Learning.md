---
tags:
  - concept
  - online_learning/theory
  - online_learning/algorithms
keywords:
  - shattering_tree
  - littlestone_dimension
topics:
  - online_learning
  - machine_learning_theory
name: Littlestone Dimension of Hypothesis Class for Online Learning
date of note: 2024-08-07
---
## Concept Definition

>[!important]
>**Name**: Littlestone Dimension of Hypothesis Class for Online Learning



## Explanation

>[!important]
>Compared to the [[Shattering of Set by Set Family]], the **(partial) ordering** $\prec$ of the *samples* $(x_{1} \,{,}\ldots{,}\,x_{T})$ plays an important role in *measuring* the shattering capability of a hypothesis class $\mathcal{H}$

- [[Tree-Order Relation]]


## Compare to VC Dimension

>[!important] Theorem
>For any class $\mathcal{H}$, $$\text{VC-dim}(\mathcal{H}) \le \text{L-dim}(\mathcal{H}),$$ and there are classes for which the **strict inequality holds**. 
>
>Furthermore, the **gap** can be *arbitrarily larger*.

- [[VC Dimension]]




-----------
##  Recommended Notes and References


- [[Shattered Tree by Hypothesis Class]]
- [[Shattering of Set by Set Family]]
- [[Shattering of Data by Function Class]]

- [[VC Dimension]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp. 248 - 251
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]]
- [[Prediction Learning and Games by Cesa-Bianchi]]