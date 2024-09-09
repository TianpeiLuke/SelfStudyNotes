---
tags:
  - concept
  - machine_learning/strategy
  - deep_learning/representation_learning
keywords:
  - contrastive_learning
  - representation_learning
topics:
  - machine_learning_strategy
  - representation_learning
name: Contrastive Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Contrastive Learning




![[contrastive_learning_framework.png]]

## Explanation

>[!quote]
>One of the most common and powerful representation learning methods is **contrastive learning** (Gutmann and Hyva ̈rinen, 2010; Oord, Li, and Vinyals, 2018; Chen, Kornblith, et al., 2020). The idea is to learn a *representation* such that certain *pairs of inputs*, referred to as **positive pairs**, are *close* in the embedding space, and *other pairs of inputs*, called **negative pairs**, are *far apart*. The intuition is that if we choose our positive pairs in such a way that they are *semantically similar* and choose negative pairs that are *semantically dissimilar*, then we will learn a representation space in which similar inputs are close, making downstream tasks, such as classification, much easier.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 191

>[!quote]
>Contrastive learning is unlike most other machine learning tasks, in that the **error function** for a given input is defined only **with respect to other inputs**, instead of having a per-input label or target output.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 191


## Examples

![[contrastive_learning_methods.png]]

- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Siamese Network for Contrastive Learning]]
- [[Noise Contrastive Estimation]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]



-----------
##  Recommended Notes and References


- [[Noise Contrastive Estimation]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]

- [[Word Embedding]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1054 - 1055
- [[Deep Learning Foundations and Concepts by Bishop]] pp 191
- Bromley, J., Guyon, I., LeCun, Y., Säckinger, E., & Shah, R. (1993). Signature verification using a" siamese" time delay neural network. _Advances in neural information processing systems_, _6_.
- Chopra, S., Hadsell, R., & LeCun, Y. (2005, June). Learning a similarity metric discriminatively, with application to face verification. In _2005 IEEE computer society conference on computer vision and pattern recognition (CVPR'05)_ (Vol. 1, pp. 539-546). IEEE.
- Hadsell, R., Chopra, S., & LeCun, Y. (2006, June). Dimensionality reduction by learning an invariant mapping. In _2006 IEEE computer society conference on computer vision and pattern recognition (CVPR'06)_ (Vol. 2, pp. 1735-1742). IEEE.
- Collobert, R., & Weston, J. (2008, July). A unified architecture for natural language processing: Deep neural networks with multitask learning. In _Proceedings of the 25th international conference on Machine learning_ (pp. 160-167).
- Weinberger, K. Q., & Saul, L. K. (2009). Distance metric learning for large margin nearest neighbor classification. _Journal of machine learning research_, _10_(2).
- Le-Khac, P. H., Healy, G., & Smeaton, A. F. (2020). Contrastive representation learning: A framework and review. _Ieee Access_, _8_, 193907-193934.
- Tian, Y., Sun, C., Poole, B., Krishnan, D., Schmid, C., & Isola, P. (2020). What makes for good views for contrastive learning?. _Advances in neural information processing systems_, _33_, 6827-6839.
- Xiao, T., Wang, X., Efros, A. A., & Darrell, T. (2020). What should not be contrastive in contrastive learning. _arXiv preprint arXiv:2008.05659_.
- Robinson, J. D., Chuang, C. Y., Sra, S., & Jegelka, S. (2021) Contrastive Learning with Hard Negative Samples. In _International Conference on Learning Representations_ (ICLR 2021).
- Li, J., Zhou, P., Xiong, C., & Hoi, S. (2021). Prototypical Contrastive Learning of Unsupervised Representations. In _International Conference on Learning Representations_ (ICLR 2021).