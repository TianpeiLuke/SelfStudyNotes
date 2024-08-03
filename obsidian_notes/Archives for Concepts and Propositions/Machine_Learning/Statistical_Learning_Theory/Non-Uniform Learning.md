---
tags:
  - concept
  - machine_learning/theory
keywords:
  - non_uniform_learning
  - Probably_Approximately_Correct
topics:
  - machine_learning_theory
name: Non-Uniform Learning
date of note: 2024-08-02
---

## Concept Definition

>[!important]
>**Name**: Non-Uniform Learning

![[PAC Learnable and Agnostic PAC Learnable#^500325]]


>[!important] Definition
>Let $\mathcal{H}$ be a hypothesis set. 
>
>$\mathcal{A}$ is an **non-uniform learning algorithm** if there exists a *polynomial function* $\text{poly}(\cdot, \cdot, \cdot, \cdot, \cdot)$  such that 
>- for any $\epsilon > 0$ and $\delta > 0$,  
>- for all distributions $\mathcal{P}$ over $\mathcal{X} \times \mathcal{Y}$,
>  
> the following holds 
>- for *any* $h \in \mathcal{H}$, 
>- *any sample size* $$m \ge \text{poly}(1/\epsilon,\, 1/\delta,\, \underline{h},\, d):$$
>$$
> \begin{align}
> \mathcal{P}\left\{ L_{\mathcal{P}}(\mathcal{A}(\mathcal{D}_{m})) - L_{\mathcal{P}}(h)  \le \epsilon \right\}  \ge 1 - \delta. 
> \end{align} 
>$$ 
>
>If $\mathcal{A}$ further runs in $$\text{poly}(1/\epsilon, 1/\delta, h, d),$$ then $\mathcal{H}$ is said to be **non-uniformly learnable**. 



## Explanation





-----------
##  Recommended Notes and References


- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]

- [[Understanding Machine Learning by Shalev-Shwartz]]