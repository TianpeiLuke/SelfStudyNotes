---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - isoperimetric_inequality
  - optimal_transport
topics:
  - concentration_inequality
  - information_theory
name: Isoperimetric Inequality via Transportation Cost
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Isoperimetric Inequality via Transportation Cost

![[Transportation Cost Inequality#^4642e4]]


- [[Transportation Cost Inequality]]

>[!important] Isoperimetric Inequality via Transportation Cost
>Consider a **metric measure space** $(\mathcal{X}, \mathscr{B}, \mathcal{P})$ with metric $d$, and suppose that $\mathcal{P}$ satisfies the **transportation cost inequality** with parameter $\nu/2 >0$
>
>
>Then for $t \ge t_0 := \sqrt{2\nu \log 2}$,  the **concentration function** satisfies the bound
>$$
> \begin{align}
> \alpha_{\mathcal{P}, (\mathcal{X}, d)}(t) &\le  \exp \left( - \frac{(t -t_0)_{+}^2}{2 \nu} \right)
> \end{align}
>$$  
>
>
>Moreover, for any $Z \sim \mathcal{P}$ and any **$L$-Lipschitz function** $f : \mathcal{X} \to \mathbb{R}$, we have the **concentration inequality** for Lipschitz function 
>$$
> \begin{align}
> \mathcal{P}\left\{ |f(Z) - \mathbb{E}_{\mathcal{P}}\left[ f(Z) \right] |  \ge t\right\} &\le 2 \exp \left( - \frac{t^2}{2 \nu L^2} \right). 
> \end{align}
>$$ 

^e1b928

- [[Concentration Function for Metric Measure Space]]

## Explanation





-----------
##  Recommended Notes and References

- [[Transportation Cost Inequality]]
- [[Information Inequalities]]

- [[Concepts and Theorems of Optimal Transport]]
- [[Wasserstein Distance]]
- [[Kullback-Leibler Divergence]]


- [[Optimal Transport Old and New by Villani]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]