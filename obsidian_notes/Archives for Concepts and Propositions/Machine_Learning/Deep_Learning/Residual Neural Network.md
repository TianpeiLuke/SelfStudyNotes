---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - residual_neural_network
  - residual_connections
  - skip_connections
keywords:
  - residual_network
topics:
  - deep_learning/models
  - deep_learning/discriminative_models
  - deep_learning/network_block
name: Residual Neural Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Residual Neural Network

![[Residual Connection for Deep Learning#^1c9b0f]]

- [[Residual Connection for Deep Learning]]


>[!important] Definition
>A **residual network** or **ResNet** consist of multiple layers of *residual blocks*
>$$
>Z^{(l)} = f(Z^{(l-1)}, W^{(l)}) + Z^{(l-1)}
>$$
>- The **gradients** in a network with *residual connections* are much **less sensitive** to input values compared to a standard deep network.
>- Note that the **skip-layer connection** in above requires the input and output to have the *same dimensionality*
>- If we want to change dimensionality, we have use additional linear map in skip connection as $$Z^{(l)} = f(Z^{(l-1)}, W^{(l)}) + W\,Z^{(l-1)}$$


![[residual_blocks.png]]

>[!important] 
>There are two ways to add residual connection
>- addition of input and *ReLU output* $$Z^{(l)} = \text{ReLU}\left(\text{MLP}(Z^{(l-1)}, W^{(l)})\right) + Z^{(l-1)}$$
>	- Note that the ReLU activation outputs are *all non-negatives*; thus the residual are all non-negatives.
>- addition of input and *linear output* $$Z^{(l)} = \text{MLP}\left(\text{ReLU}(Z^{(l-1)}, W^{(l)})\right) + Z^{(l-1)}$$
>	- This is **more commonly used**, since both positives and negatives are added.


![[resnet_connection_two_ways.png]]

- [[Convolutional Filters]]
- [[Convolutional Neural Network]]


## Explanation

>[!quote]
>Li et al. (2017) developed a way to visualize error surfaces directly, which showed that the effect of the residual connections is to create **smoother error function surfaces**,
>- It is usual to include **batch normalization layers** in a **residual network**, as together they significantly reduce the issue of vanishing and exploding gradients.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 275 - 276

- [[Batch Normalization]]

![[resnet_smooth_surface.png]]



## Network that contains Residual Blocks

### ResNet and CNN

- [[Convolutional Neural Network]]

### Transformer

- [[Transformer Network]]

### RNN

- [[Long-Short Term Memory Network or LSTM]]



-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]

- [[Hidden Markov Model]]
- [[Linear Dynamic System]]
- [[Autoregressive Models]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 368
- [[Deep Learning Foundations and Concepts by Bishop]] pp 275
- [[Foundations of Machine Learning by Mohri]] pp 357 - 358