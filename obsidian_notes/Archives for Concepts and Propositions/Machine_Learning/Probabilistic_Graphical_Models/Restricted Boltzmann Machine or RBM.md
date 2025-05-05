---
tags:
  - concept
  - machine_learning/models
  - restricted_boltzmann_machine
  - RBM
  - deep_learning/models
  - probabilistic_graphical_models/models
keywords:
  - RBM
  - restricted_boltzmann_machine
topics:
  - deep_learning/models
  - machine_learning_models
  - probabilistic_graphical_model
name: Restricted Boltzmann Machine
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Restricted Boltzmann Machine or RBM

>[!important] Definition
>A **Restricted Boltzmann Machine (RBM)** is a generative stochastic neural network that can learn a probability distribution over its set of inputs. 
>- It is an *undirected graphical model* composed of a layer of visible units $v \in \{0, 1\}^n$ and a layer of hidden units $h \in \{0, 1\}^m$, with connections only between the visible and hidden layers. 
>- There are *no* connections *within a layer*.

- [[Artificial Neural Network and Deep Learning]]
- [[Markov Network on Undirected Graph]]

### Energy Function of RBM

>[!important] Definition
>The **energy function** of an RBM for a given state $(v, h)$ is defined as:
>$$E(v, h; \theta) = -\sum_{i=1}^n a_i v_i - \sum_{j=1}^m b_j h_j - \sum_{i=1}^n \sum_{j=1}^m v_i W_{ij} h_j$$
>where $\theta = \{W, a, b\}$ are the model parameters:
>- $W$ is the $n \times m$ weight matrix connecting the *visible* and *hidden* units. $W_{ij}$ represents the weight between visible unit $i$ and hidden unit $j$.
>- $a$ is the *bias* vector for the visible units, $a_i$ is the bias of visible unit $i$.
>- $b$ is the *bias* vector for the hidden units, $b_j$ is the bias of hidden unit $j$.

- [[Energy Functional for Probabilistic Graphical Model]]


### Joint Distribution

>[!important] Definition
>The probability of a *joint configuration* $(v, h)$ is given by the **Boltzmann distribution**:
>$$P(v, h; \theta) = \frac{e^{-E(v, h; \theta)}}{Z(\theta)}$$
>where $$Z(\theta) = \sum_{v, h} e^{-E(v, h; \theta)}$$ is the *partition function*, which sums over all possible states of the visible and hidden units.

- [[Log-Partition Function and Score Function of Graphical Models]]

### Training Objective

>[!important] Definition
>The **goal** of training an RBM is to learn the parameters $\theta$ that maximize the probability of the observed data $v$. 
>- This is typically done by *maximizing the log-likelihood* of the training data.

- [[Maximum Likelihood Estimation]]

>[!important] Definition
>Due to the **bipartite structure** of the RBM, the conditional probabilities of a unit being active (equal to 1) given the state of the other layer are independent and can be easily computed:
>
>- **Probability of a hidden unit $j$ being active given the visible units $v$:**
>$$P(h_j = 1 | v; \theta) = \sigma\left(b_j + \sum_{i=1}^n v_i W_{ij}\right)$$
>where $\sigma(x) = \frac{1}{1 + e^{-x}}$ is the sigmoid activation function.
>
>- **Probability of a visible unit $i$ being active given the hidden units $h$:**
>$$P(v_i = 1 | h; \theta) = \sigma\left(a_i + \sum_{j=1}^m h_j W_{ij}\right)$$

- [[Bipartite Graph]]

### Contrastive Divergence Learning

- [[Contrastive Divergence as Approximate Markov Chain Monte Carlo]]


## Explanation


>[!important]
>RBMs can learn useful representations of the input data and can be stacked to form Deep Belief Networks (DBNs).

- [[Artificial Neural Network and Deep Learning]]

## Deep Belief Network

- [[Deep Belief Network or DBN]]


-----------
##  Recommended Notes and References


- [[Supervised Learning and Unsupervised Learning]]
- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]

- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]