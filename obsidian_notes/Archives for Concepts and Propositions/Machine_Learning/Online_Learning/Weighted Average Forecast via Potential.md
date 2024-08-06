---
tags:
  - concept
  - online_learning/algorithms
  - online_learning/theory
keywords:
  - convex_potential
  - weighted_average_algorithm
  - exponential_weighted_algorithm
topics:
  - online_learning
name: Weighted Average Forecast via Potential
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: Weighted Average Forecast via Potential

![[Regret for Online Learning#^c8c1f8]]

![[Regret for Online Learning#^7704b4]]


>[!important] Definition
>In order to minimize the regret for each expert after $T$ rounds $$R_{i, T} := \sum_{t=1}^{T}\left( \ell(\hat{y}_{t}, y_{t}) - \ell(f_{i}^{(t)}, y_{t}) \right), \; i=1\,{,}\ldots{,}\,k,$$ we can design a **weighted average algorithm** for forecaster based on a **convex potential function** $\phi: \mathbb{R} \to \mathbb{R}$.
>
>In particular,  let $$\phi: \mathbb{R} \to \mathbb{R}$$ be a a *non-negative*, *convex* and *increaseing function*, called a **potential function**. 
>
>At each round $t=1 \,{,}\ldots{,}\,T$
>- Consider the *cumulative* regret $R_{i,t-1}$ for each expert $i$ the *up to round* $t-1$, $$R_{i,t-1} := \sum_{s=1}^{t-1}\ell(\hat{y}_{s}, y_{s}) - \sum_{s=1}^{t-1}\ell(f_{i}^{(s)}, y_{s})$$
>- Define the *weight* $w_{i}^{(t)}$ for *each expert* $i$ at $t$ based on the **gradient of potential** over $R_{i,t-1}$, That is, $$w_{i}^{(t)} = \phi'(R_{i,t-1}), \quad i=1\,{,}\ldots{,}\,k.$$
>- Then the *prediction* $\hat{y}_{t}$ at time $t$ of the **weighted average forecaster** is defined by $$\hat{y}_{t} = \frac{\sum_{i=1}^{k}\phi'(R_{i,t-1})\,f_{i}^{(t)}}{\sum_{i=1}^{k}\phi'(R_{i,t-1})}$$

- [[Regret for Online Learning]]
- [[Convex Function]]

![[Potential Function for Weighted Average Forecast#^f29770]]

- [[Potential Function for Weighted Average Forecast]]

>[!important] Definition
>We can reformulate the *weighted average prediction* using above **potential function** $\Phi: \mathbb{R}^{k} \to \mathbb{R}$ as 
>$$
>\hat{y}_{t} = \frac{\sum_{i=1}^{k}\nabla \Phi \left( R_{t-1} \right)_{i}\,f_{i}^{(t)}}{\sum_{i=1}^{k}\nabla \Phi \left( R_{t-1} \right)_{i}}
>$$
>where 
>- **instantaneous regret vector** $$r_{t} := (r_{1,t} \,{,}\ldots{,}\, r_{k,t}) \in \mathbb{R}^{k}$$
>- and the **regret vector** $$R_{t} := \sum_{s=1}^{t}r_{s} := \left( \sum_{s=1}^{t}r_{1,s}\, \,{,}\ldots{,}\, \sum_{s=1}^{t}r_{k,s} \right) \in \mathbb{R}^{k}$$

### Weighted Average Forecast based on Potential

>[!important] Definition
>The **weighted average forecast** based on **potential** $\Phi$ is described as follows:
>- *Input*: outcome space $\mathcal{Y} \subset \mathbb{R}$
>- *Input*: decision space $\mathcal{D} \subset \mathbb{R}$, that is **compact** and **convex**
>- *Input*: a set of $k$ experts 
>- *Input*: a loss function $\ell: \mathcal{D} \times \mathcal{Y} \to \mathbb{R}_{+}$
>- *Input*: *potential function* $$\Phi: \mathbb{R}^{k} \to \mathbb{R}$$
>- For $t = 1\,{,}\ldots{,}\,T$:
>	- Collect the **cumulative regret vector** for all experts up to $t-1$ $$R_{t-1} := (R_{1,t-1} \,{,}\ldots{,}\,R_{k, t-1})$$
>	- Each *expert* $i=1\,{,}\ldots{,}\,k$ **predicts** $f_{i}^{(t)}\in \mathcal{D}$
>	- Compute the *weight* for expert $i=1\,{,}\ldots{,}\,k$  based on **gradient of potentials** $$w_{i}^{(t)} := \nabla \Phi \left( R_{t-1} \right)_{i}$$
>	- Compute the **weighted average** of experts' predictions $$\hat{y}_{t} = \frac{\sum_{i=1}^{k}w_{i}^{(t)}\,f_{i}^{(t)}}{\sum_{i=1}^{k}w_{i}^{(t)}}$$
>	- *Observe* outcome $y_{t}\in \mathcal{Y}$
>	- Compute the **instantaneous regret** for expert $i=1\,{,}\ldots{,}\,k$ $$r_{i,t} = \ell(\hat{y}_{t}, y_{t}) - \ell(f_{i}^{(t)}, y_{t})$$
>	- Update the **cumulative regret** for expert $i=1\,{,}\ldots{,}\,k$  $$R_{i, t} = R_{i, t-1} + r_{i,t}.$$ 




## Explanation


## Incremental Gradient Descent

>[!info]
>The above **weighted average algorithm** can be seen as the **incremental gradient algorithm** that solves 
>$$
>\min_{r_{1} \,{,}\ldots{,}\, r_{k}} \sum_{i=1}^{k}\phi \left( \sum_{s=1}^{T}r_{i,s} \right) 
>$$
>where $r_i = (r_{i,s})_{s=1}^{T}.$

- [[Incremental Gradient Algorithm]]
- [[Gradient Descent Algorithm]]





## Examples

### Exponential Weighted Average

![[Potential Function for Weighted Average Forecast#^57afc0]]

>[!important] Definition
>The **exponential weighted average** algorithm is the *weighted average forecast* with potential 
>$$
>\Phi(u; \eta) := \frac{1}{\eta}\log \left( \sum_{i=1}^{k}\exp \left( \eta\, u_{i} \right) \right)
>$$
>
>- The **weight** is computed as
>$$
>w_{i}^{(t)} = \nabla \Phi \left( R_{t-1}; \eta \right)_{i} = \frac{\exp \left( \eta\, R_{i, t-1} \right)}{\sum_{i=1}^{k}\exp \left( \eta\, R_{i, t-1} \right)}
>$$
>- The **weighted average prediction** is 
> $$
>\begin{align*}
>\hat{y}_{t} &= \frac{\sum_{i=1}^{k}\exp \left( \eta\, \left( \widehat{L}_{t-1} - L_{i, t-1} \right)  \right)\,f_{i}^{(t)}}{\sum_{i=1}^{k}\exp \left( \eta\, \left( \widehat{L}_{t-1} - L_{i, t-1} \right)  \right)\,}\\[10pt]
>&= \frac{\sum_{i=1}^{k}\exp \left( - \eta\, L_{i, t-1}\right)\,f_{i}^{(t)}}{\sum_{i=1}^{k}\exp \left( - \eta\,L_{i, t-1}   \right)\,}
\end{align*}
> $$
>- An important characteristic for the **EWA** is that the forecast *only depends* on the *past performance of* **experts** $L_{i, t-1}$.
>	- It is *independent* from the **past predictions** $\hat{y}_{t}$ and its cumulative loss $\widehat{L}_{t-1}.$
>- Moreover, the *weight* can be updated using **previous weight** only. $$w_{i}^{(t)} = \frac{w_{i}^{(t-1)}\exp \left(-\eta\, \ell(f_{i}^{(t-1)}, y_{t}) \right)}{\sum_{i=1}^{k}w_{i}^{(t-1)}\exp \left(-\eta\, \ell(f_{i}^{(t-1)}, y_{t}) \right)}$$

^668a02

- [[Exponential Weighted Algorithm for Convex Loss]]




-----------
##  Recommended Notes and References


- [[Potential Function for Weighted Average Forecast]]
- [[Regret for Online Learning]]
- [[Exponential Weighted Algorithm for Convex Loss]]
- [[Online Prediction with Expert Advice]]


- [[Convex Function]]
- [[Convex Optimization Problem]]


- [[Prediction Learning and Games by Cesa-Bianchi]] pp 9