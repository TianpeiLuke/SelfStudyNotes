---
tags:
  - concept
  - machine_learning/ensemble_methods
  - machine_learning/theory
keywords:
  - bagging_ml
  - model_averaging_ml
topics:
  - machine_learning/ensemble_methods
name: Bagging and Model Averaging
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: Bagging and Model Averaging

>[!important] Definition
>Let $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n}$. Denote $\mathcal{F}_{\Theta}$ be the model space parameterized by $\theta\in \Theta$. 
>
>Let $\hat{f}_{\theta, \mathcal{D}}\in \mathcal{F}_{\Theta}$ be a model trained using data from $\mathcal{D}$. Consider the task of learning $f_{\theta}\in \mathcal{F}_{\Theta}$.
>
>The **bagging method** or **boostrap averaging** method is described as below:
>- *Require*: the dataset  $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n}$
>- *Require*: the model class $\mathcal{F}_{\Theta}$
>- *Require*: a *learning algorithm* $\mathcal{A}: \mathcal{D} \to \mathcal{F}_{\Theta}$
>- *Require*: total rounds $T >0$
>- For $t=1\,{,}\ldots{,}\,T$:
>	- **Bootstrap resampling**: select a *sub-population* by resampling with repetition from $\mathcal{D}$ $$\mathcal{D}^{t}\sim \mathcal{D}$$
>	- **Learning**: train a new model based on *sub-population* $\mathcal{D}^{t}$  $$\hat{f}_{\theta, \mathcal{D}^{t}} = \mathcal{A}(\mathcal{D}^{t})$$
>- **Averaging / Majority Vote**: obtain the *bagging estimate* based on *averaging* all model outputs for *subpopulations* $$\hat{f}_{bag}(x) := \frac{1}{T}\sum_{t=1}^{T}\hat{f}_{\theta, \mathcal{D}^{t}}(x)$$

^56f716

- [[Bootstrap Method]]
- [[Ensemble Learning]]

### Random Forest

- [[Random Forest Algorithm]]


## Explanation

>[!info]
>The **bagging estimation** $\hat{f}_{bag}$  is different from a model trained on all data $\hat{f}_{\theta, \mathcal{D}}$ *only when* the function class $\mathcal{F}_{\Theta}$ is **nonlinear.**

>[!important] 
>Let $$P_{n} := \frac{1}{n}\sum_{i=1}^{n}\delta_{x_{i}, y_{i}}$$ be the *empirical measure* for $\mathcal{D} := \left\{ (x_{i}, y_{i})\right\}_{i=1}^{n}$.
>
>The **true Bagging estimate** is given by $$f_{bag} :=  \mathbb{E}_{\mathcal{D}^{t} \sim P_{n}}\left[ \hat{f}_{\theta, \mathcal{D}^{t}} \right]$$
>
>It can be shown that as $T\to \infty$
>$$
>\hat{f}_{bag} := \frac{1}{T}\sum_{t=1}^{T}\hat{f}_{\theta, \mathcal{D}^{t}} \to \mathbb{E}_{\mathcal{D}^{t} \sim P_{n}}\left[ \hat{f}_{\theta, \mathcal{D}^{t}} \right], \quad \forall x
>$$

- [[Empirical Process and Empirical Measure]]
- [[Glivenko-Cantelli Theorem]]

>[!important]
>The main use of **bagging** is to **reduce the variance** of estimation. 
>- for instance, **bagging decision trees** as common.
>- It is not necessary to produce better results. 
>- It depends on the performance of *learning algorithm*.

- [[Bias-Variance Tradeoff]]

>[!quote] Wisdom of Grounds
>The *collective* knowledge of **diverse** and **independent** body of people typically *exceeds* the knowledge of any individual and can be *harnessed* by **voting.** 

>[!info]
>The models $\hat{f}_{\mathcal{D}^{t}}$ learned from *resampled subpopulation* $\mathcal{D}^{t}\sim \mathcal{D}$ are **not independent.**

>[!info] 
>One of **disadvantages** for **Bagging** is that we lose **interpretability** of the model. 
>
>The decision boundary is **nonsmooth.**



## Other Ensemble Methods

### Mixture of Gaussian

- [[Gaussian Mixture Models]]
- [[Gaussian Scale Mixtures]]

### Bootstrap Methods

- [[Bootstrap Method]]
- [[Particle Filter or Sampling-Importance-Resampling]]

### Model Average in Neural Network

- [[Dropout for Deep Learning]]

### Boosting

>[!info]
>Compared to **boosting**, each learned model $\hat{f}_{\mathcal{D}^{t}}$ are obtained **in parallel** with each model trained **independently** using sampled population **prior** to training. 
>
>In **boosting** such as AdaBoost, the subpoluation is sampled based on **prediction from previous model**.

- [[AdaBoost Algorithm]]
- [[Gradient Boosting Trees]]
- [[Gradient Boosting Algorithm]]


-----------
##  Recommended Notes and References



- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]




- [[Elements of Statistical Learning by Hastie]] pp 282 - 288, 409, 587
- [[Boosting Foundations and Algorithms by Schapire]] pp 118 - 120
- [[Deep Learning by Goodfellow]] pp 249
- [[Deep Learning Foundations and Concepts by Bishop]] pp 277 - 279
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 651