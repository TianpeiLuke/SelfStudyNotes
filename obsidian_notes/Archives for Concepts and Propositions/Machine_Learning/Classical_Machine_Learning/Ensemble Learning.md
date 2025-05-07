---
tags:
  - concept
  - machine_learning/models
  - machine_learning/strategy
  - machine_learning/theory
  - machine_learning/ensemble_methods
  - ensemble_learning
keywords:
  - ensemble_method
topics:
  - machine_learning_models
  - machine_learning_strategy
name: Ensemble Learning
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Ensemble Learning

>[!important] Definition
>**Ensemble learning** is a technique in machine learning where *multiple* “base” models—often referred to as *learners* or *experts*—are trained and *combined* to solve a single prediction task. 
>- By aggregating the strengths and compensating for the weaknesses of individual models, ensembles typically achieve *higher accuracy*, *greater robustness*, and *better generalization* than any single constituent.

## Explanation

>[!info]
>Common strategies include 
>- **bagging** (e.g., random forests), which trains each model on a different bootstrap sample and *averages* their predictions to reduce variance;
>- **boosting** (e.g., AdaBoost, Gradient Boosting), which *sequentially* trains models to focus on examples that previous ones misclassified and then weights their votes; 
>- and **stacking**, which learns how to best combine the outputs of diverse base learners using a “*meta‐learner*.”

>[!info]
>Ensemble methods are widely used in competitions and real‐world applications because they tend to be more resilient to overfitting and can adapt to a variety of data distributions.

## Ensemble Learning Methods

### Bagging

- [[Bagging and Model Averaging]]

### Boostrap

- [[Bootstrap Method]]

### Gaussian Mixtures

- [[Gaussian Mixture Models or GMM]]
- [[Gaussian Scale Mixtures]]

### Dropout in Deep Learning

- [[Dropout for Deep Learning]]

### Boosting

- [[AdaBoost Algorithm]]
- [[Gradient Boosting Algorithm]]
- [[Gradient Boosting Trees]]

### Mixture of Experts





-----------
##  Recommended Notes and References


- [[Bagging and Model Averaging]]



- [[Boosting Foundations and Algorithms by Schapire]]  pp 5
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Artificial Intelligence Modern Approach by Russell]] pp 748 - 752