---
tags:
  - concept
  - machine_learning/theory
  - statistics/concentration_inequality
keywords:
  - generalization_error
  - concentration_empirical_process
topics:
  - machine_learning_theory
  - concentration_inequality
name: Generalization Error Bound for Binary Classification Finite Case
date of note: 2024-08-01
---

## Concept Definition

>[!important]
>**Name**: Generalization Error Bound for Binary Classification Finite Case

![[Empirical Risk Minimization#^a84128]]

![[Empirical Risk Minimization#^c9ebc0]]

![[PAC Learnable and Agnostic PAC Learnable#^500325]]

### Consistent Case

>[!important] Proposition
>Let $\mathcal{H}$ be a **finite set** of functions mapping from $\mathcal{X}$ to $\mathcal{Y}$. Let $\mathcal{A}$ be an algorithm that for any **target concept** $c \in \mathcal{H}$ and i.i.d. sample $\mathcal{D}_n$ returns a **consistent hypothesis** $h_{n}$, i.e. *the training error* of $h_{n}$ is *zero*: $$L_{\mathcal{D}_{n}}(\mathcal{A}(\mathcal{D}_{n}))  = L_{\mathcal{D}_{n}}(h_{n}) = 0.$$
>
> Then, for any $\epsilon, \delta > 0$, the inequality 
>$$ 
> \begin{align*}
> \mathcal{P}\set{ L_{\mathcal{P}, c}(\mathcal{A}(\mathcal{D}_{n})) \le \epsilon} &\ge  1 - \delta
> \end{align*}
>$$  
>*holds if*
>$$
> \begin{align}
> n &\ge \frac{1}{\epsilon}\log \left( \frac{\lvert \mathcal{H} \rvert }{\delta} \right) = \frac{1}{\epsilon}\left( \log|\mathcal{H}| + \log \frac{1}{\delta} \right)
> \end{align}
>$$
> 
> This sample complexity result admits the following **equivalent statement** as a **generalization bound**: 
> 
>-  for any $\epsilon, \delta > 0$, with *probability at least* $1 - \delta$,
> $$
> \begin{align}
> L_{\mathcal{P}, c}(h_{n}) &\le \frac{1}{n}\log \left( \frac{\lvert \mathcal{H} \rvert }{\delta} \right) =  \frac{1}{n}\left( \log|\mathcal{H}| + \log \frac{1}{\delta} \right).
> \end{align}
>$$ 

^5bf1f1

- [[Realizability Assumption for Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]


### Inconsistent Case

>[!important] Proposition
>Let $\mathcal{H}$ be a **finite set** of functions mapping from $\mathcal{X}$ to $\mathcal{Y}$.  
>
>Then, for any $\delta > 0$ with *probability at least* $1 - \delta$, the following inequality holds for the **generalization error**: for all $h \in \mathcal{H}$
>$$
> \begin{align}
>  L_{\mathcal{P}}(h) \le L_{\mathcal{D}}(h) + \sqrt{\frac{\log|\mathcal{H}| + \log\dfrac{2}{\delta}}{2m}}  
> \end{align}
>$$  
>
>Thus for a **finite hypothesis set** $\mathcal{H}$, 
>$$
> \begin{align}
> L_{\mathcal{P}}(h)  \le  L_{\mathcal{D}}(h)  + O\left( \sqrt{\frac{\log|\mathcal{H}|}{m}} \right)
> \end{align}
>$$ 

^ac9f27

- [[Hoeffding Inequality]]



## Explanation





-----------
##  Recommended Notes and References


- [[Realizability Assumption for Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Generalization Error Bound for Binary Classification VC Dimension]]
- [[Empirical Risk Minimization]]
- [[Hoeffding Inequality]]

- [[Generalization Error Bound for AdaBoost Finite Case]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]] pp 17