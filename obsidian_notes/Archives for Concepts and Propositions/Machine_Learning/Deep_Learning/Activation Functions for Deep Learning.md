---
tags:
  - concept
  - machine_learning/models
  - deep_learning/architecture
  - activation_functions
  - sigmoid_functions
  - rectified_linear_units
  - relu_functions
keywords:
  - activation_function
  - deep_learning
topics:
  - deep_learning/network_block
name: Activation Functions for Deep Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Activation Functions for Deep Learning

![[activation_function.png]]

### Identity Activation Functions

>[!quote]
>The simplest option for a *hidden unit activation function* is the **identity function**, which means that all the hidden units become linear. However, for any such network, we can always find an equivalent network without hidden units. This follows from the fact that the **composition** of successive **linear transformations** is itself a **linear transformation**, and so its representational capability is no greater than that of a single linear layer. However, if the number of **hidden units** is **smaller** than either the number of *input or output units*, then the transformations that such a network can generate are not the most general possible linear transformation from inputs to outputs because information is *lost* in the **dimensionality reduction** at the hidden units. ... Such "*bottleneck*" networks of linear units corresponds to a standard data analysis technique called **principal component analysis**. In general, however, there is limited interest in using multilayer networks of linear units since the overall function computed by such a network is still linear.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 183

- [[Principal Component Analysis]]

### Sigmoid Activation Function

![[Sigmoid Function as Activation for Deep Learning#^69ebf2]]

![[Sigmoid Function as Activation for Deep Learning#^dd6afc]]

![[Sigmoid Function as Activation for Deep Learning#^e7c130]]

![[Sigmoid Function as Activation for Deep Learning#^175d87]]

![[Sigmoid Function as Activation for Deep Learning#^72bb2e]]

- [[Sigmoid Function as Activation for Deep Learning]]


### Rectified Linear Unit

![[Rectified Linear Unit as Activation for Deep Learning#^8da7d6]]


![[Rectified Linear Unit as Activation for Deep Learning#^8b0ae0]]


![[Rectified Linear Unit as Activation for Deep Learning#^bea432]]


- [[Rectified Linear Unit as Activation for Deep Learning]]

## Explanation

>[!quote]
>We have seen that the **activation functions** for the *output units* are determined by the kind of distribution being modelled. For the *hidden units*, however, the only requirement is that they need to be *differentiable*, which leaves a wide range of possibilities. In most cases, all the hidden units in a network will be given the same activation function, although in principle there is no reason why different choices could not be applied in different parts of the network.





-----------
##  Recommended Notes and References



- [[Artificial Neural Network and Deep Learning]]
- [[Back-Propagation Algorithm]]
- [[Perceptron Algorithm]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Elements of Statistical Learning by Hastie]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] 
- [[Deep Learning Foundations and Concepts by Bishop]] pp 183 - 185