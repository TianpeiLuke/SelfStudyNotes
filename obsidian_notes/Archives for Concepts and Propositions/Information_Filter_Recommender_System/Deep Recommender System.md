---
tags:
  - concept
  - recommender_system/information_filter
  - deep_recommender_system
keywords:
  - deep_recommender_system
topics:
  - recommender_system
name: Deep Recommender System
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Deep Recommender System

>[!important] Definition
>A **deep recommender system** applies modern deep-learning architectures to the classic problem of matching *users with items*—movies, products, songs—by automatically learning high-capacity representations and interaction functions from *massive implicit-feedback logs*.

- [[Recommender System]]
- [[Artificial Neural Network and Deep Learning]]
- [[User-Item Preference and Rating for Recommendation]]

### Training

>[!info]
>Training typically minimises a **ranking** or **implicit-cross-entropy loss** on billions of *user-item interactions*, 
>- often with 
>	- **negative-sampling** 
>	- or **pairwise contrastive objectives**, 
>- while techniques like 
>	- **two-tower architectures**, 
>	- **sampling-based softmax**, 
>	- and **ANN vector search** 
>
>keep both offline learning and real-time retrieval tractable. 

- [[Siamese Network or Twin Tower Network for Contrastive Learning]]
- [[Contrastive Learning]]
- [[Approximate Nearest Neighbor Search]]
- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]


>[!info]
>The result is a unified model that captures 
>- collaborative signals, 
>- content semantics 
>- and contextual factors, 
>
>enabling personalised recommendation at web scale and powering platforms like YouTube’s candidate generation, TikTok’s “For You”, and Amazon’s product feed—albeit with challenges in bias, data drift and explainability that remain active research areas.



## Explanation

>[!info]
>Instead of hand-crafted *factorisation models* that embed users and items with linear dot-products, deep approaches feed **sparse IDs**, **textual metadata** or **images** through embedding layers and one or more neural blocks 
>- MLPs
>- CNNs 
>- RNNs, 
>- transformers, 
>- graph nets
>
>so the system can model complex nonlinear patterns such as 
>- **sequential taste drift**, 
>- **cross-feature conjunctions** 
>- and **cold-start content cues**.

- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Convolutional Neural Network]]
- [[Recurrent Neural Network]]
- [[Transformer Network]]
- [[Graph Neural Network]]

## Examples






-----------
##  Recommended Notes and References


- **[RecBole](https://recbole.io/)** – Unified framework for deep recommenders
- [[Recommender Systems Textbook by Aggarwal]] pp 8, 29, 72