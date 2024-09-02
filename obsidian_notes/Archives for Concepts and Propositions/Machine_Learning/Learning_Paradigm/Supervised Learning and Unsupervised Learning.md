---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/models
  - machine_learning/paradigm
keywords:
  - unsupervised_learning
  - supervised_learning
topics:
  - machine_learning_paradigm
name: Supervised Learning and Unsupervised Learning
date of note: 2024-08-10
---

## Concept Definition

>[!important]
>**Name**: Supervised Learning and Unsupervised Learning

### Supervised Learning

>[!important]
>**Supervised learning** algorithms are, roughly speaking, learning algorithms that learn to *associate* some *input* with some *output*, given a training set of examples of inputs $x$ and outputs $y$.

>[!important] Definition
>Most of supervised learning algorithm estimate the *conditional probability* of output $y$ given input $x$ $$\mathcal{P}(Y\,|\,X)$$ assuming that $(X, Y)\in \mathcal{X}\times \mathcal{Y}$ is sample from distribution $\mathcal{P}(X, Y).$
>
>This paradigm is called the **probabilistic supervised learning**.
 
- [[Empirical Risk Minimization]]
- [[Conditional Probability]]

>[!important] Definition
>The **non-probabilistic supervised learning** directly learn a function $h\in \mathcal{H}$ so that the error under $\mathcal{P}$ is minimized
>$$
>h \in \arg\inf_{h\in \mathcal{H}}\left\{ \mathbb{E}_{ p }\left[ L(h(X), Y)  \right] + \lambda\,\Omega \left(\lVert h \rVert  \right)\right\} 
>$$

### Unsupervised Learning

>[!quote]
>**unsupervised algorithms** are those that experience only “features” but not a supervision signal. The distinction between supervised and unsupervised algorithms is not formally and rigidly defined because there is no objective test for distinguishing whether a value is a feature or a target provided by a supervisor.
>
>-- [[Deep Learning by Goodfellow]] pp 142

>[!important] 
>Informally, **unsupervised learning** refers to most attempts to *extract information from a distribution* that do not require human labor to annotate examples. The term is usually associated with *density estimation*, learning to draw samples from a distribution, learning to denoise data from some distribution, finding a *manifold* that the data lies near, or *clustering* the data into groups of related examples.




## Explanation


## Examples

### Supervised Learning Algorithms

- [[k Nearest Neighbor Classification]]
- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Logistic Regression]]
- [[Support Vector Machine]]
- [[AdaBoost Algorithm]]
- [[Gradient Boosting Algorithm]]
- [[Artificial Neural Network and Deep Learning]]
- [[Naive Bayes Model]]
- [[Conditional Random Field]]
- [[Multi-Armed Adversarial Bandit]]
- [[Upper Confidence Bound Algorithm]]
- [[EXP3 or Exponential Weights Algorithm for Exploration and Exploitation]]

### Unsupervised Learning Algorithm

- [[k-Means Clustering]]
- [[Principle Component Analysis]]




-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Boosting Foundations and Algorithms by Schapire]]
- [[Deep Learning by Goodfellow]] pp 136
- [[Deep Learning Foundations and Concepts by Bishop]]