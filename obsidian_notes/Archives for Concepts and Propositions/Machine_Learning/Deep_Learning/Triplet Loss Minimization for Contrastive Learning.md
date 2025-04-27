---
tags:
  - concept
  - deep_learning/representation_learning
  - deep_learning/contrastive_learning
  - triplet_loss_minimization
  - contrastive_learning
  - triplet_loss
  - representation_learning
keywords:
  - triplet_loss
  - contrastive_learning
topics:
  - deep_learning/contrastive_learning
  - representation_learning
name: Triplet Loss Minimization for Contrastive Learning
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: Triplet Loss Minimization for Contrastive Learning

![[Contrastive Learning#^9b383a]]

- [[Contrastive Learning]]

>[!important] Definition
>Let $X$ be an *anchor point*, and $p^{+}$ and $p^{-}$ be a positive sample pair and a negative sample pair.
>
>The goal of **metric learning** is to learn an *embedding* $f(x)$ such that 
>- $X$ and $X^{+}$ are *close* in *embedding space*, while
>-  $X$ and $X^{-}$ are *far apart* in embedding space.
>
>
>The **triplet loss** is defined as the following
>$$
>\begin{align*}
> &L_{\text{triplet}}(\theta) \\[5pt]
> &=  \mathbb{E}_{ X, X^{+}, X^{-} }\left[  \max\left\{0,\; \lVert f_{\theta}(X) - f_{\theta}(X^{+}) \rVert_{2}^2 -  \lVert f_{\theta}(X) - f_{\theta}(X^{-}) \rVert_{2}^2 + \epsilon \right\}  \right]
>\end{align*}
>$$
>- This loss tries to ensure the *positive pair* $p^{+}$ is always *at least some distance* $\epsilon$ *closer* to each other than the *negative pair* $p^{-}$
>- The distance metric in embedding space can be replaced by other metrics $d$
>- The general triplet loss is given by $$\mathbb{E}_{ X, X^{+}, X^{-} }\left[  \max\left\{0,\; d_{f}(X, X^{+})^2 - d_{f}(X, X^{-})^2 + \epsilon \right\}  \right]$$
>  

^3609c4

- [[Metric Learning]]
- [[Margin-based Loss Function]]

### Pair Loss

>[!important] Definition
>An alternative definition for **contrastive loss** is defined as the following
>$$
>\begin{align*}
> &L_{\text{contrastive}}(\theta) \\[5pt]
> &= \left\{ \begin{array}{{ll}}d_{f}(X, k)^2 & \text{ if } k\sim p^{+}(\cdot|X)\\[5pt] \max\left\{0\,,\, \epsilon - d_{f}(X, k)^2\right\}  & \text{ if } k\sim p^{-}(\cdot|X)  \end{array}\right. 
>\end{align*}
>$$

^0cd056

- Chopra, S., Hadsell, R., & LeCun, Y. (2005, June). Learning a similarity metric discriminatively, with application to face verification. In _2005 IEEE computer society conference on computer vision and pattern recognition (CVPR'05)_ (Vol. 1, pp. 539-546). IEEE.
- [[Margin-based Loss Function]]


## Explanation

>[!info]
>A **downside** to the triplet loss approach is that one has to be **careful** about choosing **hard negatives**: 
>- if the negative pair is already sufficiently far away then the objective function is zero and no learning occurs.

- Robinson, J. D., Chuang, C. Y., Sra, S., & Jegelka, S. (2021) Contrastive Learning with Hard Negative Samples. In _International Conference on Learning Representations_ (ICLR 2021).






-----------
##  Recommended Notes and References


- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Siamese Network or Twin Tower Network for Contrastive Learning]]

- [[Contrastive Learning]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1056
- [[Foundations of Computer Vision by Torralba]] pp 457
- Chopra, S., Hadsell, R., & LeCun, Y. (2005, June). Learning a similarity metric discriminatively, with application to face verification. In _2005 IEEE computer society conference on computer vision and pattern recognition (CVPR'05)_ (Vol. 1, pp. 539-546). IEEE.
- Hadsell, R., Chopra, S., & LeCun, Y. (2006, June). Dimensionality reduction by learning an invariant mapping. In _2006 IEEE computer society conference on computer vision and pattern recognition (CVPR'06)_ (Vol. 2, pp. 1735-1742). IEEE.
- Collobert, R., & Weston, J. (2008, July). A unified architecture for natural language processing: Deep neural networks with multitask learning. In _Proceedings of the 25th international conference on Machine learning_ (pp. 160-167).
- Weinberger, K. Q., & Saul, L. K. (2009). Distance metric learning for large margin nearest neighbor classification. _Journal of machine learning research_, _10_(2).