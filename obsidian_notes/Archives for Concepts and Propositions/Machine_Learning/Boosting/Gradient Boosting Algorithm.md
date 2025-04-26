---
tags:
  - concept
  - machine_learning/models
  - machine_learning/boosting
  - machine_learning/ensemble_methods
  - gradient_boost
keywords:
  - gradient_boost
topics:
  - boosting
  - machine_learning_models
name: Gradient Boost Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gradient Boosting Algorithm

![[Functional Gradient Descent#^a70b99]]


>[!important] Definition
>The **Gradient Boost** algorithm is described as the following:
>- *Require*: a collection of **labeled data** $\mathcal{D}:=\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \mathcal{Y}$
>- *Require*: a **hypothesis class** $\mathcal{H}: \mathcal{X}\to \mathcal{Y}$
>- *Require*:  a **loss functional** $\mathcal{L}: \mathcal{H} \to \mathbb{R}_{+}$
>- For $t = 1 \,{,}\ldots{,}\,T$:
>	- Compute the **residuals** as the *negative gradient* of *loss functional* on $\mathcal{D}$, i.e. $$r_{t}(i) :=  - \frac{ \partial \mathcal{L}(\cdot; \mathcal{D})}{ \partial F}(F_{t}(x_{i})) := - \frac{ \partial \mathcal{L}}{ \partial F(x_{i})}(F_{t}(x_{i})), \quad i=1\,{,}\ldots{,}\,m$$
>	- Select a **weak hypothesis** $h_{t} \in \mathcal{H}$ to *minimize* a **regression loss** where the **pseudo-labels** are $r_{t}$, i.e. $$h_{t} \in \arg\max_{h\in \mathcal{H}} \;\sum_{i=1}^{m}\left( h(x_{i}) - r_{t}(i) \right)^2 $$
>	- Choose **rate** $\alpha_{t}$ via *line search* which satisfies $$\mathcal{L}(F_{t} + \alpha\, h_{t}; \mathcal{D}) \le \mathcal{L}(F_{t}; \mathcal{D}) + c_{1}\,\alpha\, \left\langle h_{t} , \nabla \mathcal{L}(F_{t};\mathcal{D}) \right\rangle_{\mathcal{H}, \mathcal{D}}$$ for some $c_{1} \in  (0,1).$
>		  
>- *Output* the *final hypothesis* by a **weighted combination** of all learned weak hypotheses: $$F_{T}(x) = \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x).$$

^dad77c

- [[Functional Gradient Descent]]
- [[Line Search Strategies for Optimal Stepsize]]
- [[Regression Problem]]

## Explanation


## AdaBoost

![[AdaBoost Algorithm#^1982f3]]

- [[AdaBoost Algorithm]]









-----------
##  Recommended Notes and References

- [[Functional Gradient Descent]]
- [[Gradient Boosting Trees]]

- [[chenXGBoostScalableTree2016]]
- [[keLightGBMHighlyEfficient2017]]

- [What makes LightGBM lightning fast?](https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e)

- [[Boosting Foundations and Algorithms by Schapire]] pp 188 - 193
- [[Elements of Statistical Learning by Hastie]] pp 358 - 361
