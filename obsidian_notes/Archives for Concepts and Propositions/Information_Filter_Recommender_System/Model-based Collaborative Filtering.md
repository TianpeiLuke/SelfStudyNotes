---
tags:
  - concept
  - recommender_system/information_filter
  - machine_learning/dimensionality_reduction
  - model_based_collaborative_filtering
  - model_based_CF
keywords:
  - model_based_collaborative_filtering
topics:
  - recommender_system
name: Model-based Collaborative Filtering
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Model-based Collaborative Filtering

>[!important] Definition
>**Model-Based Collaborative Filtering** is an approach to recommendation systems where predictive models are trained on the *user-item interaction* data to learn *latent patterns* and *generalize* beyond observed ratings or behaviors. 
>- Instead of relying directly on *memory* of past interactions, model-based methods build 
>	- an *abstract representation*—such as latent factors, embeddings, 
>	- or *predictive functions*—that can *estimate the preference* of a user for unseen items. 

- [[Collaborative Filtering]]
- [[Memory-based Collaborative Filtering]]
- [[User-Item Preference and Rating for Recommendation]]


## Explanation

>[!important]
>- **Pros**
>	- Model-based collaborative filtering typically offers 
>		- *better scalability*, 
>		- *robustness to data sparsity*, 
>		- and *higher-quality recommendations* compared to memory-based methods
>- **Cons**
>	- it often requires a *training phase* and careful regularization to prevent overfitting.


- [[Memory-based Collaborative Filtering]]

## Model-based Collaborative Filtering Methods

 >[!info]
>Common techniques include 
>- **matrix factorization** (e.g., SVD, ALS), 
>	- [[Singular Value Decomposition of Linear Map]]
>	- [[Nonnegative Matrix Factorization]]
>- **probabilistic models**, 
>	- [[Naive Bayes Model]]
>	- [[Multinomial Naive Bayes Model]]
>	- [[Latent Variable Models]]
>	- [[Gaussian Process Latent Variable Model]]
>- **deep learning architectures** (e.g., neural collaborative filtering), 
>	- [[Deep Recommender System]]
>- and **graph-based methods**. 



-----------
##  Recommended Notes and References


- [[Graph]]

- [[Recommender Systems Textbook by Aggarwal]] pp 29 - 69