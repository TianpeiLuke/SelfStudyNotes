---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
  - dropout
  - dropout_deep_learning
  - ensemble_learning
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

>[!important] Definition
>The **dropout** technique is used as a *regularization method* that reduces the number of active edges when training on each sample.
>
>Specifically, for each *weight* edge $w_{i,j}^{(l)}$ that connects the node $i$ in layer $l$ and node $j$ in layer $l+1$, the **dropout** multiplies it with random number $\epsilon_{i}^{(l)}$ for all $j$, i.e. the weight becomes $$\epsilon_{i}^{(l)}w_{i,j}^{(l)}, \quad \text{ where } \epsilon_{i}^{(l)}\sim \text{Ber}(1-p), \quad \forall j$$ where $p$ is the **drop probability.**
>- If $\epsilon_{i}^{(l)} = 0$, then *all weights out of unit* $i$ in layer $l$ will be set to zero.
>- The collection of all $$E := \left\{ \epsilon_{i}^{(l)}, \forall i,\; \forall l \right\} $$ forms a **mask**.

- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Bernoulli Distribution]]

>[!info]
>Given a binary vector $d$, we have the family of submodels as 
>$$
>p(y|\,v, d) := \text{softmax}\left(W^{T}\,\left(d \odot v\right) + b\right)
>$$

- [[Hadamard Product of Matrices]]


>[!important] Definition
>During the **training** with **dropout**, 
>- For each sample $x_{n}$:
>	- **Resample** $\epsilon_{i}^{(l)}\sim \text{Ber}(1-p), \quad \forall i\in N_{l}, \forall l$
>	- If  $\epsilon_{i}^{(l)} = 0$: 
>		- **Switch off** *gradient* for weights $w_{i,j}^{(l)}$ for all $j\in N_{l+1}$, i.e. *set* $$\frac{ \partial L }{ \partial w_{i,j}^{(l)} } = 0, \quad \forall j\in N_{l+1}$$


![[dropout_murphy.png]]

### Testing

#### Monte Carlo Dropout

>[!important] Definition
>Once training is complete, predictions can in principle be made by applying the **ensemble rule**
>$$
>p(y \,|\, x) = \sum_{E}\,p(y\,|\,x, E)\,p(E)
>$$
>where $E$ is the *sampled mask* for each iteration of training.
>- The sum is over the *exponentially large space of possible masks*.
>- This summation is intractable but can be approximated via **Monte Carlo methods**, which is known as the **Monte Carlo dropout.**

#### Rescaling in Testing

>[!important] Definition
>One simpler technique for *dropout* in testing is 
>- to make predictions with trained network with **no nodes masked out**, 
>- and to **re-scale the weights** so that the expected input to each node is roughtly the same during **testing** as it would be during the training.
>  
>If a node $i$ is present with *probability* $\rho$ in *training*, then in **testing** the output weights from that node $w_{i,j}^{(l)}$ will multiply by $\rho$ before prediction $$w_{i,j}^{(l)} \to w_{i,j}^{(l)}\,\rho$$ 


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

![[dropout_deep_learning.png]]

### Compare with Ensemble Methods

>[!info]
>If the data points are grouped into *mini-batches* then the gradients are *averaged* over the data points in each mini-batch **before** *applying the weight update*. 
>- For a network with $M$ *non-output nodes*, there are $$2^M$$ *pruned networks*, and so only a small fraction of these networks will ever be considered during training.
>- This differs from **conventional ensemble methods** in which each of the networks in the ensemble is *independently trained* to convergence. 
>- Another difference is that the **exponentially many networks** that are *implicitly being trained* with dropout are **not independent** but **share their parameter** values with the full network, and hence with each other.
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 280  

- [[Ensemble Learning]]

### Bayesian Learning

>[!quote]
>A different motivation for dropout comes from the **Bayesian perspective**. 
>
>In a fully Bayesian treatment, we would make predictions by *averaging over all possible $2^M$ network models*, with each network weighted by its **posterior probability**. Computationally, this would be *prohibitively expensive*, both during training when evaluating the posterior probabilities and during testing when computing the weighted predictions. 
>
>**Dropout** *approximates* this model averaging by giving an *equal weight* to each possible model.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 281



### Dropout Regularization for Overfit Reduction

>[!quote]
>Neural networks often have millions of parameters, and thus can sometimes *overfit*, especially when trained on small datasets. There are many ways to ameliorate this effect, such as applying regularizers to the weights, or adopting a fully Bayesian approach (see Chapter 17). Another common *heuristic* is known as **dropout** [Sri+14a], in which edges are *randomly omitted* each time the network is used, as illustrated in Figure 16.5.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627 - 628

>[!quote]
>Further intuition behind dropout comes from its role in **reducing over-fitting**. In a standard network, the parameters can become tuned to noise on individual data points, with hidden nodes becoming *over-specialized*. Each node adjusts its weights to minimize the error, given the outputs of other nodes, leading to **co-adaptation of nodes** in a way that might *not generalize* to new data. 
>
>With **dropout**, each node *cannot rely on* the presence of *other specific nodes* and must instead make useful contributions in a broad range of contexts, thereby reducing co-adaptation and specialization. For a simple linear regression model trained using least squares, **dropout regularization** is equivalent to a modified form of **quadratic regularization**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 281

- [[Ridge Regression and L2 Regularization]]





-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]
- [[Ensemble Learning]]
- [[lambda-Return and Compound Update]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627 - 628
- [[Deep Learning Foundations and Concepts by Bishop]] pp 279
- [[Deep Learning by Goodfellow]] pp 251 - 260
