---
tags:
  - concept
  - deep_learning/representation_learning
  - deep_learning/contrastive_learning
  - siamese_network
  - twin_networks
  - twin_tower_network
keywords:
  - siamese_network
  - contrastive_learning
  - representation_learning
topics:
  - deep_learning/contrastive_learning
name: Siamese Network for Contrastive Learning
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: Siamese Network for Contrastive Learning

>[!important] Definition
>The **Siamese Network** is a type of neural network architecture designed to learn meaningful representations by *comparing pairs* of inputs.


- [[Cosine Similarity and Cosine Distance]]
- [[Contrastive Learning]]
- [[Soft Weight Sharing for Deep Learning]]
- [[Convolutional Neural Network]]

### Architecture

>[!important] Definition
> A **Siamese Network** consists of *two identical subnetworks* (called "**twin networks**") that *share the same parameters* and architecture.
>  - Each subnetwork takes an input (e.g., $x_1$ and $x_2$) and maps it to a *feature embedding* via a *shared* function:
>    $$
>    f(x;\theta): \mathcal{X} \to \mathbb{R}^{d},
>    $$
>    where $\theta$ represents the shared parameters.
>  - The two embeddings are then compared using a *distance function* (e.g., Euclidean distance, cosine similarity) or fed into a classifier head to predict similarity.
>



### Contrastive Loss

>[!important] Definition
>The network is trained on *pairs* of examples labeled as either *similar* or **dissimilar**.
>
> Common loss functions include:
>    - **Contrastive Loss**: encourages similar pairs to have embeddings close together, and dissimilar pairs to be far apart:
>      $$
>      \mathcal{L} = (1 - y) \cdot \frac{1}{2} \left( D(f(x_1), f(x_2)) \right)^2 + y \cdot \frac{1}{2} \left( \max(0, m - D(f(x_1), f(x_2))) \right)^2,
>      $$
>      where $D(\cdot, \cdot)$ is a distance metric, $y \in \{0,1\}$ is the pair label, and $m$ is a margin.
>    - **Binary Cross Entropy Loss** (for similarity prediction): if the network outputs a probability score.


- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Noise Contrastive Estimation]]



## Explanation

>[!important]
> **Key Features**:
>  - **Parameter sharing** ensures that similar inputs are mapped into a similar embedding space.
>  - Designed to learn a **general notion of similarity**, rather than classifying inputs individually.
>  - Can be used in **zero-shot** or **few-shot** settings, where training and testing classes differ.

### Compare with InfoNCE and Triplet Loss Minimization


| Feature            | **Siamese Network**                     | **Triplet Network**                              | **InfoNCE** (SimCLR/MoCo)                      |
| ------------------ | --------------------------------------- | ------------------------------------------------ | ---------------------------------------------- |
| Network            | 2 towers (shared)                       | 3 towers (shared)                                | Many samples encoded                           |
| **Basic Unit**     | (positive, negative) pair               | (anchor, positive, negative) triplet             | Positive + negatives in batch                  |
| **Supervision**    | Binary similarity labels                | Relative ranking constraint                      | Self-supervised or weak labels                 |
| **Loss type**      | Contrastive loss                        | Margin-based triplet loss                        | Softmax-based InfoNCE loss                     |
| **Focus**          | *Absolute* *similarity*/dissimilarity   | *Relative* distance *ordering*                   | Discriminative *representations*               |
| Typical use        | Verification tasks (face ID, signature) | Fine-grained *metric learning* (face clustering) | Self-supervised pretraining (vision, language) |
| Sampling challenge | Many pairs needed                       | Hard triplet mining important                    | Need large batches or memory banks             |

- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]

## Application

### Locality Sensitive Hashing

- [[Locality-Sensitive Hashing or LSH for ANN Search]]

### Sentence-BERT

- [[Sentence-BERT for Sentence Embedding]]

### Dense Retrieval

- [[Dense Text Retrieval with Pretrained Language Models]]




-----------
##  Recommended Notes and References


- [[Representation Learning]]
- [[Supervised Learning and Unsupervised Learning]]
- [[Canonical Correlation Analysis]]


- Wikipedia [Siamese neural network](https://en.wikipedia.org/wiki/Siamese_neural_network)

- Bromley, J., Guyon, I., LeCun, Y., Säckinger, E., & Shah, R. (1993). Signature verification using a" siamese" time delay neural network. _Advances in neural information processing systems_, _6_.
- Chicco, D. (2021). Siamese neural networks: An overview. _Artificial neural networks_, 73-94.