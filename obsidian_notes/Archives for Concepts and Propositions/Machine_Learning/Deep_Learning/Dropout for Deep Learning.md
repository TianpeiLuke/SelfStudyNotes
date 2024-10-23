---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - dropout_deep_learning
  - ensemble_method
topics:
  - deep_learning/regularization
name: Dropout for Deep Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Dropout for Deep Learning




![[dropout_deep_learning.png]]




## Explanation

>[!quote]
>**Dropout** (Srivastava et al., 2014) provides a *computationally inexpensive* but *powerful* method of *regularizing a broad family of models*. 
>- To a first approximation, dropout can be thought of as a method of making **bagging** practical for *ensembles of very many large neural networks*. 
>- **Bagging** involves training *multiple models* and evaluating multiple models on *each test example*. 
>	- This seems impractical when each model is a large neural network, since training and evaluating such networks is costly in terms of runtime and memory. 
>	- It is common to use ensembles of five to ten neural networks—Szegedy et al. (2014a) used six to win the ILSVRCbut more than this rapidly becomes unwieldy. 
>- Dropout provides an **inexpensive approximation** to training and evaluating a bagged ensemble of exponentially many neural networks.
>  
>-- [[Deep Learning by Goodfellow]] pp 251  

- [[Ensemble Learning]]




-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]
- [[Ensemble Learning]]
- [[lambda-Return and Compound Update]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627
- [[Deep Learning Foundations and Concepts by Bishop]] pp 279
- [[Deep Learning by Goodfellow]] pp 251
