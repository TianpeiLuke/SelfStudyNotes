---
tags:
  - concept
  - machine_learning/strategy
  - deep_learning/representation_learning
keywords:
  - representation_learning
topics:
  - machine_learning_strategy
  - deep_learning
  - representation_learning
name: Representation Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Representation Learning

![[Distributed Representation#^04ca19]]

- [[Distributed Representation]]

>[!important] Definition
>**Representation learning** is a **paradigm** for *training* machine learning models to *transform* raw inputs into a form that makes it *easier* to solve new tasks.
>- Unlike supervised learning, where the task is known at training time, representation learning often *assumes* that we *do not know* what *task* we wish to solve ahead of time.
>
>The learned representation, sometimes called the **embedding space** 

- [[Word Embedding]]
- [[Supervised Learning and Unsupervised Learning]]


## Explanation

### Distributed Representation

>[!quote]
>Many information processing tasks can be very easy or very difficult depending on **how the information is represented**.
>
>-- [[Deep Learning by Goodfellow]] pp 517

- [[Three Components of Intelligence System]]

>[!quote]
>Several key concepts arose during the connectionism movement of the 1980s that remain central to today’s deep learning.  
>
>One of these concepts is that of **distributed representation** (Hinton et al., 1986). This is the idea that *each input* to a system should be *represented by many features*, and *each feature* should be involved in the *representation of many possible inputs*. 
>
>-- [[Deep Learning by Goodfellow]] pp 16


>[!quote]
>Many deep learning algorithms are motivated by the assumption that the *hidden units* can learn to *represent the underlying causal factors* that explain the data. Distributed representations are natural for this approach, because each *direction* in **representation space** can correspond to the value of a *different underlying configuration variable*.
>
>-- [[Deep Learning by Goodfellow]] 536


### Representation Learning


>[!quote]
>We can view the successive layers of a deep neural network as performing *transformations of the data*, that make it easier to solve the desired task or tasks. For example, a neural network that successfully learns to classify skin lesions as benign Section 1.1.1 or malignant must have learned to transform the original image data into a new space, represented by the outputs of the final layer of hidden units, such that the final layer of the network can distinguish the two classes. This final layer can be viewed as a *simple linear classifier*, and so in the representation of the last hidden layer, the two classes must be well separated by a linear surface. This ability to *discover a nonlinear transformation* of the data that makes subsequent tasks easier to solve is called **representation learning** (Bengio, Courville, and Vincent, 2012). The learned representation, sometimes called the **embedding space**, is given by the outputs of one of the hidden layers of the network, so that any input vector, either from the training set or from some new data set, can be transformed into this representation by forward propagation through the network. 
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 188


### Unsupervised Learning

>[!quote]
>Representation learning is especially powerful because it allows us to *exploit unlabelled data*. Often it is easy to collect a large quantity of unlabelled data, but acquiring the associated labels may be more difficult. For example, a video camera on a vehicle can gather large numbers of images of urban scenes as the vehicle is driven around a city, but taking those images and identifying relevant objects, such as pedestrians and road signs, would require expensive and time-consuming human labelling.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 188


>[!quote]
>Most **representation learning problems** face a **trade-off** between **preserving** as much *information* about the input as possible and **attaining nice properties** (such as independence).  
>
>Representation learning is particularly interesting because it provides one way to perform *unsupervised and semi-supervised learning*. We often have very large amounts of unlabeled training data and relatively little labeled training data. Training with supervised learning techniques on the labeled subset often results in severe overfitting. *Semi-supervised learning* offers the chance to resolve this overfitting problem by also learning from the unlabeled data. Specifically, we can *learn good representations* for the *unlabeled data*, and then use these representations to solve the *supervised learning task*.

- [[Supervised Learning and Unsupervised Learning]]


## Greedy Layer-wise Unsupervised Pretraining

>[!quote]
>**Unsupervised pretraining** combines two different ideas. 
>- First, it makes use of the idea that the **choice of initial parameters** for a deep neural network can have a significant **regularizing effect** on the model (and, to a lesser extent, that it can improve optimization). 
>- Second, it makes use of the more general idea that **learning about** the *input distribution* can help with learning about the *mapping from inputs to outputs*.
>  
>-- [[Deep Learning by Goodfellow]] pp 521 - 522  



>[!quote]
>Historically, **unsupervised learning** played an important role in enabling the first deep networks (apart from convolutional networks) to be successfully trained. Each layer of the network was first **pre-trained** using unsupervised learning and then the entire network was trained further using gradient-based supervised training. It was later discovered that the *pre-training phase could be omitted* and a deep network could be trained from scratch purely using supervised learning given appropriate conditions.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 189

- [[Restricted Boltzmann Machine]]

## Self-Supervised Learning

- [[Self-Supervised Learning]]


## Fine-Tuning



## Disentanglement




## Similarity of Representation

- [[Contrastive Learning]]
- [[Canonical Correlation Analysis]]

## Transfer Learning

- [[Transfer Learning]]


## Examples

### Non-distributed Representation

- [[k-Means Clustering]]
- [[k Nearest Neighbor Classification]]
- [[Gradient Boosting Trees]]
- [[Gaussian Mixture Models]]
- [[Reproducing Kernel Hilbert Space]]
- [[Gaussian Process]]
- [[RKHS of Gaussian Process]]
- [[Multinomial Principle Component Analysis]]


### Latent Variable Model

- [[Latent Variable Models]]
- [[Factor Analysis]]
- [[Principle Component Analysis]]
- [[Probabilistic Principle Component Analysis]]
- [[Independent Component Analysis]]
- [[Nonnegative Matrix Factorization]]

- [[Gaussian Process Latent Variable Model]]

### Auto-Encoder

- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Denoising Auto-Encoder]]
- [[Sparse Auto-Encoder and Regularized Auto-Encoder]]
- [[Contractive Auto-Encoder]]
- [[Variational Auto-Encoder]]


### Graphical Model

- [[Restricted Boltzmann Machine]]
- [[Conditional Random Field]]
- [[Gaussian Graphical Model]]

### Dynamic System

- [[State-Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Linear Dynamic System]]
- [[Dynamic Bayesian Network]]
- [[Hidden Markov Model]]
- [[Kalman Filter Discrete-Time]]

- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network]]
- [[Gated Recurrent Units in Neural Network]]



### Transformers

- [[Transformer Network]]





-----------
##  Recommended Notes and References


- [[Distributed Representation]]
- [[Supervised Learning and Unsupervised Learning]]
- [[Three Components of Intelligence System]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 709,  774, 1039 - 1064
- [[Deep Learning Foundations and Concepts by Bishop]] pp 188 - 189
- [[Probabilistic Graphical Models by Koller]]
- [[Deep Learning by Goodfellow]] pp 3, 16, 147, 517 - 549