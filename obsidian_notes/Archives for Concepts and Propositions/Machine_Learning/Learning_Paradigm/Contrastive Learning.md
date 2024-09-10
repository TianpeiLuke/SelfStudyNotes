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


>[!important] Definition
>Intuitively, **contrastive representation learning** or **contrastive learning** can be considered as **learning by comparing**. 
>-  Unlike a discriminative model that learns a mapping to some (pseudo-)labels and a generative model that reconstructs input samples, in contrastive learning a representation is learned by comparing among the input samples.
>
>Instead of learning a signal from *individual data samples* *one at a time*, contrastive learning learns by *comparing among different samples*. 
>- The comparison can be performed between **positive pairs** of ‘‘similar’’ inputs and **negative pairs** of ‘‘dissimilar’’ inputs.
>  
>  
>By **contrasting** between samples of *positive* and samples of *negative pairs*, 
>- *representations* of *positive pairs* will be *pulled together* while 
>- representations of *negative pairs* are *pushed far apart*.  

^c13422

- Le-Khac, P. H., Healy, G., & Smeaton, A. F. (2020). Contrastive representation learning: A framework and review. _Ieee Access_, _8_, 193907-193934.



>[!important] Definition
>Let $X$ be a sample, called **anchor point**.  
>
>A set of samples $\left\{ X_{i}^{+} \right\}$ that are *similar to* $X$ are called **positive samples**, and a set of samples $\left\{ X_{j}^{-} \right\}$ that are *dissimilar to* $X$ are called **negative samples**.
>- A pair of anchor point and positive sample $p^{+} = (X, X_{i}^{+})$ is called a **positive pair**. It is assume that $$X_{i}^{+} \sim p^{+}(\cdot|X)$$ where $p^{+}(\cdot|x)$ is a positive data generation process.
>- A pair of anchor point and negative sample $p^{-} = (X, X_{i}^{-})$ is called a **negative pair**. $$X_{i}^{-} \sim p^{-}(\cdot|X)$$ where $p^{-}(\cdot|x)$ is a negative data generation process.

^9b383a

>[!important] Definition
>Considering the problem of similarity matching as dictionary lookup, we can adopted the notion of *query* and *key* for contrastive learning.
>
>Let $\mathcal{X}$ be a sample space. 
>- A **query** $X\in \mathcal{X}$ is a particular **view** of sample in $\mathcal{X}$. We denote query as $q$.
>- A **key** $k\in \mathcal{X}$ is also a particular **view** of sample in $\mathcal{X}$. 
>	- A query-key pair $(q, k^{+})$ is called **positive pair** if the key $k^{+}$ is considered *similar to query* $q$;
>	- A query-key pair $(q, k^{-})$ is called **negative pair** if the key $k^{-}$ is considered *dissimilar to query* $q$;
>	  


### A Framework for Contrastive Learning

- Le-Khac, P. H., Healy, G., & Smeaton, A. F. (2020). Contrastive representation learning: A framework and review. _Ieee Access_, _8_, 193907-193934.


>[!important] Definition
>A **similarity distribution** $p^{+}(q, k^{+})$ is a joint distribution over a pair of samples that formalizes the notion of **similarity** (and *dissimilarity*) in the *contrastive learning task*.
>- Note that instead of defining data distribution $p(x)$, the similarity required takes input from *joint distribution* $p(q, k)$
>- A negative key is drawn from **dissimilar distribution** $p^{-}(q, k^{-})$

>[!important] Definition
>A **encoder** $e_{\eta}: \mathcal{X} \to \mathcal{V} \subset \mathbb{R}^{d}$ maps the input in $\mathcal{X}$ into *feature representation* in $\mathbb{R}^{d}.$
>- Feature encoder can be used in multiple tasks.
>  
>Then the feature representation is mapped into *metric representation* for *comparison* via a **metric transform** $$f_{\theta}: v \mapsto z\in \mathbb{R}^{s}.$$


>[!important] Definition
>A **contrastive loss function** operates on a set of metric embedding pairs $${(z,  z^{+}), (z, z^{-})}$$ of the *query, positive and negative keys*. 
>- It measures the **similarity** (or distance) between the **embeddings** and 
>- It enforces **constraints** such that the *similarity of positive pairs* are *high* and the *similarity of negative pairs* are *low*.

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

### Multiview Representation Learning

- [[Multi-view Learning]]

>[!quote]
>The members of positive and negative pairs do not necessarily have to come from the same data modality. In **contrastive-language image pretraining**, or **CLIP** (Radford et al., 2021), a positive pair consists of an image and its corresponding text caption, and two separate functions, one for each modality, are used to map the inputs to the same representation space. *Negative pairs* are then *mismatched images and captions*. This is often referred to as **weakly supervised**, as it relies on captioned images, which are often easier to obtain by scraping data from the internet than by manually labelling images with their classes.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 192

![[Information Noise Contrastive Estimation as Contrastive Learning#^56fa08]]


### Metric Learning

- [[Metric Learning]]

### Self-Supervised Learning

- [[Self-Supervised Learning]]

![[contrastive_generative_discriminative.png]]


## Contrastive Loss Functions

![[contrastive_learning_methods.png]]

![[Triplet Loss Minimization for Contrastive Learning#^0cd056]]


![[Triplet Loss Minimization for Contrastive Learning#^3609c4]]

- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Siamese Network for Contrastive Learning]]

![[Information Noise Contrastive Estimation as Contrastive Learning#^c99f51]]


- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Noise Contrastive Estimation]]

## Choose Negative Samples

>[!quote]
>A particular contrastive learning algorithm is defined predominantly by **how the positive and negative pairs are chosen**, which is how we use our *prior knowledge* to specify what a good representation should be. For example, consider the problem of learning representations of images. Here, a common choice is to create positive pairs by corrupting the input images in ways that should preserve the semantic information of the image while greatly altering the image in the pixel space (Wu et al., 2018; He et al., 2019; Chen, Kornblith, et al., 2020). Corruptions are closely related to **data augmentations**, and examples include *rotation, translation, and colour shifts*. Other images from the data set can then be used to create the negative pairs. This approach to contrastive learning is known as **instance discrimination**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 192





-----------
##  Recommended Notes and References


- [[Noise Contrastive Estimation]]
- [[Triplet Loss Minimization for Contrastive Learning]]
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