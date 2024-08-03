---
tags:
  - concept
  - statistics/concentration_inequality
  - math/stochastic_process
  - machine_learning/theory
keywords:
  - rademacher_complexity
topics:
  - machine_learning_theory
  - concentration_inequality
name: Rademacher Complexity Bound for Binary Classification
date of note: 2024-07-30
---

## Concept Definition

>[!important]
>**Name**: Rademacher Complexity Bound for Binary Classification

![[Empirical Risk Minimization#^a84128]]

![[Empirical Risk Minimization#^cf1946]]

>[!important] Lemma (Rademacher Complexity for 0-1 Loss)
>Let $\mathcal{H}$ be a family of functions taking values in $\{-1, +1\}$ and let $\mathcal{G}$ be the family of loss functions associated to $\mathcal{H}$ for the **binary loss**: 
>$$
> \begin{align*}
> \mathcal{G} := \{(x,y) \mapsto \mathbb{1}_{h(x) \neq y}:  h \in \mathcal{H} \}.
> \end{align*}
>$$ 
> For any sample $\mathcal{D} = ((X_1, Y_1) \,{,}\ldots{,}\, (X_n, Y_n))$ of elements in $\mathcal{X} \times \{-1, +1\}$, let $\mathcal{D}_{\mathcal{X}} := (X_1 \,{,}\ldots{,}\, X_n)$. 
> 
> Then, the following relation holds between **the empirical Rademacher complexities** of $\mathcal{G}$ and $\mathcal{H}$:
>$$ 
> \begin{align*}
> \widehat{\mathfrak{R}}_{\mathcal{D}}(\mathcal{G}) &\le \frac{1}{2}\widehat{\mathfrak{R}}_{\mathcal{D}_{\mathcal{X}}}(\mathcal{H})
> \end{align*}
>$$  
>This implies that $$\mathfrak{R}(\mathcal{G}) = \frac{1}{2}\mathfrak{R}(\mathcal{H}).$$ 


- [[Rademacher Complexity]]
- [[Symmetrization Technique for Empirical Process]]
- [[Symmetrization Inequalities for Empirical Process]]
- [[Symmetrized Empirical Process]]


![[Uniform Bound via Rademacher Complexity#^5276e2]]


>[!important] Proposition (Rademacher Complexity Bound for Binary Classification)
> Let $\mathcal{H}$ be a family of **binary functions** taking values in $\{-1, +1\}$  and let $\mathcal{P}$ be the distribution over the input space $\mathcal{X}$. 
> 
> Then, for any $\delta > 0$, *with probability at least* $1 - \delta$ over a sample $\mathcal{D}_{n}$ of size $n$ drawn according to $\mathcal{P}$, each of the following holds for *any* $h \in \mathcal{H}$, the **generalization error** of $h$ is *bounded above* by **empirical error** and **Rademacher complexity**  
>$$ 
> \begin{align}
> L_{\mathcal{P}}(h) &\le L_{\mathcal{D}_{n}}(h) + \mathfrak{R}_{n}(\mathcal{H}) + \sqrt{\frac{\log(1 / \delta)}{2n}} 
> \end{align}
>$$
>and
>$$
> \begin{align}
> L_{\mathcal{P}}(h) &\le L_{\mathcal{D}_{n}}(h) + \widehat{\mathfrak{R}}_{n}(\mathcal{H}) +  3\sqrt{\frac{\log(2 / \delta)}{2n}}. 
>\end{align} 
>$$

^d66865

- [[Empirical Risk Minimization]]
- [[Uniform Bound via Rademacher Complexity]]



## Explanation





-----------
##  Recommended Notes and References


- [[Rademacher Complexity]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Uniform Bound via Rademacher Complexity]]
- [[Rademacher Complexity Upper Bound for Suprema of Empirical Process]]

- [[Foundations of Machine Learning by Mohri]] pp 34 - 38
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]