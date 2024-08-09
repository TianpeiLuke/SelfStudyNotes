---
tags:
  - concept
  - machine_learning/theory
  - optimization/theory
keywords:
  - regularization
  - tikhonov_regularization
topics:
  - machine_learning_theory
name: Tikhonov Regularization in Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Tikhonov Regularization in Optimization

![[Regularized Loss Minimization#^494e48]]


>[!important] Definition
>Throughout this section we will focus on one of the most simple regularization functions: $$R(h)=\lambda \lVert h \rVert_{\mathcal{H}}^2,$$ where $\lambda > 0$ is a scalar and the *norm* is the $L_{2}$ norm. 
>
>The *regualarized loss minimization problem* becomes:
>$$
> \begin{align}
> \mathcal{A}(\mathcal{D}) = \arg\min_{h \in \mathcal{H}}\left\{   L_{\mathcal{D}}(h) + \lambda \lVert h \rVert_{\mathcal{H}}^2\right\}. 
> \end{align}
>$$   
>
>This type of regularization function is often called **Tikhonov regularization** or **$L_{2}$ regularization**.
>
>For a parameterized hypothesis class by *finite dimension parameter space* $$h_{w} \in \mathcal{H} \mapsto w\in C \subset \mathbb{R}^{d},$$ the *Tikhonov regularization* term becomes the $\ell_{2}$ norm regularization term, 
>$$
>\arg\min_{w \in C}\left\{   L_{\mathcal{D}}(w) + \lambda \lVert w \rVert_{2}^2\right\}. 
>$$

- [[Regularized Loss Minimization]]
- [[Structural Risk Minimization]]


## Explanation





-----------
##  Recommended Notes and References

- [[Empirical Risk Minimization]]
- [[Regularized Loss Minimization]]


- [[Proximal Algorithm]]
- [[Generalized Proximal Method]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 138
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 221
- [[Deep Learning Foundations and Concepts by Bishop]] pp 253