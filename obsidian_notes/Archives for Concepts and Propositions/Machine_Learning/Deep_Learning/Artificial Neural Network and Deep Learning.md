---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
keywords:
  - artificial_neural_network
  - deep_learning
topics:
  - deep_learning/models
  - deep_learning/algorithm
name: Artificial Neural Network and Deep Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Artificial Neural Network and Deep Learning

>[!quote]
>It is easiest to understand deep learning with some historical context. Rather than providing a detailed history of deep learning, we identify a few key trends:  
>- Deep learning has had a *long and rich history*, but has gone by **many names**, reflecting different philosophical viewpoints, and has waxed and waned in popularity. 
>- Deep learning has become more useful as the **amount of available training data has increased**.  
>- Deep learning models have grown in size over time as **computer infrastructure** (both hardware and software) for deep learning has improved.  
>- Deep learning has solved increasingly complicated applications with increasing accuracy over time.
>  
>-- [[Deep Learning by Goodfellow]] pp 11

>[!important]
>The **central idea** in *connectionism* is that **a large number** of **simple computational units** can achieve *intelligent behavior* when networked together. This insight applies equally to *neurons* in biological nervous systems as it does to hidden units in computational models.
>
>-- [[Deep Learning by Goodfellow]] pp 16

>[!important]
>Several *key concepts* arose during the connectionism movement of the 1980s that remain central to today’s deep learning.  
>
>One of these concepts is that of **distributed representation** (Hinton et al., 1986). This is the idea that *each input* to a system should be represented by *many features*, and *each feature* should be involved in the representation of *many possible inputs*.
>
>Another major accomplishment of the connectionist movement was the successful use of **back-propagation** to train deep neural networks with internal representations and the popularization of the back-propagation algorithm (Rumelhart et al., 1986a; LeCun, 1987). This algorithm has waxed and waned in popularity but, as of this writing, is the dominant approach to training deep models.
>
>-- [[Deep Learning by Goodfellow]] pp 16 - 17





## Explanation

>[!important]
>Broadly speaking, there have been three waves of development: 
>- deep learning known as **cybernetics** in the *1940s–1960s*, 
>- deep learning known as **connectionism** in the *1980s–1990s*, and 
>- the current resurgence under the name **deep learning** beginning in 2006.
>
>-- [[Deep Learning by Goodfellow]] pp 12  

### From Neural Science to Computer Science

>[!quote]
>Some of the earliest learning algorithms we recognize today were intended to be computational models of biological learning, that is, models of how learning happens or could happen in the brain. As a result, one of the names that deep learning has gone by is **artificial neural networks (ANNs).** The corresponding perspective on deep learning models is that they are engineered systems inspired by the *biological brain* (whether the human brain or the brain of another animal). While the kinds of neural networks used for machine learning have sometimes been used to understand brain function (Hinton and Shallice, 1991), they are generally **not designed to be realistic models of biological function**. The neural perspective on deep learning is motivated by **two main ideas**. One idea is that the brain provides a proof by example that **intelligent behavior is possible**, and a conceptually straightforward path to building intelligence is to *reverse engineer* the computational principles behind the brain and duplicate its functionality. Another perspective is that it would be deeply interesting to **understand the brain** and the **principles that underlie human intelligence**, so machine learning models that shed light on these basic scientific questions are useful apart from their ability to solve engineering applications.
>
>- [[Deep Learning by Goodfellow]] pp 13 


>[!quote]
>Today, neuroscience is regarded as an important source of inspiration for deep learning researchers, but it is **no longer the predominant guide** for the field.
>
>The **main reason** for the diminished role of neuroscience in deep learning research today is that we simply *do not have enough information* about the brain to use it as a guide. To obtain a deep understanding of the actual algorithms used by the brain, we would need to be able to monitor the activity of (at the very least) thousands of interconnected neurons simultaneously. Because we are not able to do this, we are far from understanding even some of the most simple and well-studied parts of the brain. 
>
>-- [[Deep Learning by Goodfellow]] pp 15



## Activation Functions in Deep Learning

- [[Activation Functions for Deep Learning]]


## Loss Function for Deep Learning

- [[Error Function or Loss Function for Deep Learning]]

## Basic Building Blocks

### Feedforward Layer

- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Activation Functions for Deep Learning]]
- [[Loss Function in Deep Learning]]

### Normalization Layer

- [[Batch Normalization]]
- [[Layer Normalization]]

### Convolution Layer

- [[Convolutional Filters]]
- [[Pooling for Deep Learning]]

### Recurrent Layer

- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network]]

### Residual Connection

- [[Residual Connection for Deep Learning]]

### Attention Layer and Transformer

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]





-----------
##  Recommended Notes and References




- [[Back-Propagation Algorithm]]
- [[Perceptron Algorithm]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Elements of Statistical Learning by Hastie]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] 
- [[Deep Learning Foundations and Concepts by Bishop]] 