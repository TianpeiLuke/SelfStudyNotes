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
- [[Classification Problem]]
- [[Regression Problem]]
- [[Ranking as Learning Problem]]

>[!important] Definition
>The **non-probabilistic supervised learning** directly learn a function $h\in \mathcal{H}$ so that the error under $\mathcal{P}$ is minimized
>$$
>h \in \arg\inf_{h\in \mathcal{H}}\left\{ \mathbb{E}_{ p }\left[ L(h(X), Y)  \right] + \lambda\,\Omega \left(\lVert h \rVert  \right)\right\} 
>$$

>[!important] Definition
>In **supervised learning**, the learning task is done in *batch mode*: we collect a batch of *labeled* training samples, and then a model is learned based on the *batched training set*.
>
>This is in contrast to the **reinforcement learning** and the **online learning** where the *labels* or *feedbacks* are collected in *sequential manner*  and the model is learned *while* feedbacks are collected.



### Unsupervised Learning

>[!quote]
>**unsupervised algorithms** are those that experience only “features” but not a supervision signal. The distinction between supervised and unsupervised algorithms is not formally and rigidly defined because there is no objective test for distinguishing whether a value is a feature or a target provided by a supervisor.
>
>-- [[Deep Learning by Goodfellow]] pp 142

>[!important] 
>Informally, **unsupervised learning** refers to most attempts to *extract information from a distribution* that do not require human labor to annotate examples. The term is usually associated with *density estimation*, learning to draw samples from a distribution, learning to denoise data from some distribution, finding a *manifold* that the data lies near, or *clustering* the data into groups of related examples.

>[!important] Definition
>**Unsupervised learning** deals with datasets that consist only of input features without any explicit labels or targets. 
>- Its aim is to uncover *hidden structure or patterns* in the data, such as 
>	- grouping similar points, 
>	- reducing dimensionality, or 
>	- modeling the data distribution. 

>[!info]
>Unsupervised learning is particularly valuable for exploratory data analysis, anomaly detection, and as a pretraining step to capture representations that can be fine-tuned for downstream supervised tasks. 


## Explanation

>[!info]
>Unsupervised Learning techniques include 
>- **clustering methods** (e.g., k-means, hierarchical clustering), 
>- **dimensionality-reduction methods** (e.g., PCA, t-SNE, autoencoders), 
>- **density estimation** (e.g., Gaussian mixture models), 
>- and **generative models** (e.g., GANs, variational autoencoders). 

## Examples

### Supervised Learning Algorithms

- [[k Nearest Neighbor Classification]]
- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Logistic Regression]]
- [[Support Vector Machine Linear Separable Case]]
- [[Support Vector Machine General with Soft-Margin Relaxation]]
- [[Support Vector Machine Kernel Expansion and RKHS]]
- [[Decision Tree Model for Classification and Regression]]
- [[Random Forest Algorithm]]
- [[AdaBoost Algorithm]]
- [[Gradient Boosting Algorithm]]
- [[Gradient Boosting Trees]]
- [[Artificial Neural Network and Deep Learning]]
- [[Convolutional Neural Network]]
- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Gated Recurrent Units in Neural Network]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Transformer Network]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Guided Diffusion Model and Conditional Diffusion Model]]
- [[Bayesian Neural Network]]
- [[Probabilistic Graphical Models]]
- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]
- [[Conditional Random Field]]
- [[Prediction with Expert Advice]]
- [[epsilon-Greedy Algorithm]]
- [[Multi-Armed Adversarial Bandit]]
- [[Explore-Then-Commit Bandit Algorithm]]
- [[Upper Confidence Bound Algorithm]]
- [[EXP3 or Exponential Weights Algorithm for Exploration and Exploitation]]
- [[Follow-The-Leader Algorithm]]
- [[Follow-The-Regularized-Leader Algorithm]]
- [[Perceptron Algorithm]]



### Unsupervised Learning Algorithm

- [[k-Means Clustering]]
- [[Spectral Clustering]]
- [[Gaussian Mixture Models]]
- [[Gaussian Scale Mixtures]]
- [[Principal Component Analysis]]
- [[Probabilistic Principal Component Analysis]]
- [[Kernel Principal Component Analysis]]
- [[Factor Analysis]]
- [[Gaussian Process Latent Variable Model]]
- [[Multinomial Principle Component Analysis]]
- [[Latent Dirichlet Allocation]]
- [[k Nearest Neighbor Density Estimation]]
- [[Parzen Kernel Density Estimation]]
- [[Probabilistic Graphical Models]]
- [[Gaussian Graphical Model]]
- [[Dynamic Bayesian Network]]
- [[Kalman Filter Discrete-Time]]
- [[Hidden Markov Model]]
- [[Artificial Neural Network and Deep Learning]]
- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Gated Recurrent Units in Neural Network]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Variational Auto-Encoder]]
- [[t-SNE as Dimensionality Reduction]]
- [[Transformer Network]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Continuous-Time Diffusion Network via Stochastic Differential Equations]]
- [[Normalizing Flows]]
- [[Generative Adversarial Network]]
- [[f-Generative Adversarial Network]]
- [[Wasserstein Generative Adversarial Network]]





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