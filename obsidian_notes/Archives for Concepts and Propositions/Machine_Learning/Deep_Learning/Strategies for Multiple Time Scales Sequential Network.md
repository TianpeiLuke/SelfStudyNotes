---
tags:
  - concept
  - deep_learning/models
  - deep_learning/sequential_networks
keywords:
  - residual_connection
  - vanishing_gradient
  - exploding_gradient
  - recurrent_neural_network
  - attention_network
topics:
  - deep_learning/sequential_networks
name: Strategies for Multiple Time Scales Sequential Network
date of note: 2024-09-02
---

## Concept Definition

>[!important]
>**Name**: Leaky Units and Other Strategies for Multiple Time Scales Sequential Network

### Adding Skip Connections through Time

![[Residual Connection for Deep Learning#^259204]]

- [[Residual Connection for Deep Learning]]

### Leaky Units

![[Rectified Linear Unit as Activation for Deep Learning#^8b0ae0]]

![[Rectified Linear Unit as Activation for Deep Learning#^9ae94a]]

- [[Rectified Linear Unit as Activation for Deep Learning]]

### Removing Connections

![[Vanishing and Exploding Gradient Problems for Sequential Networks#^1610ad]]

- [[Vanishing and Exploding Gradient Problems for Sequential Networks]]

>[!quote]
>Another approach to handling **long-term dependencies** is the idea of organizing the **state** of the RNN **at multiple time scales** (El Hihi and Bengio, 1996), with information flowing more easily through long distances at the *slower time scales*. 
>
>This idea differs from the **skip connections through time** discussed earlier because it involves actively **removing length-one connections** and replacing them with **longer connections**. Units modified in such a way are forced to operate on a long time scale. 
>- Skip connections through time add edges. Units receiving such new connections may learn to operate on a long time scale but may also choose to focus on their other, short-term connections.
>  
>-- [[Deep Learning by Goodfellow]] pp 396  


### Attention Mechanism

![[Attention Mechanism in Neural Network#^ad8f13]]

![[Attention Mechanism in Neural Network#^cc46d7]]

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]

## Explanation





-----------
##  Recommended Notes and References


- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Residual Neural Network]]

- [[Recurrent Neural Network]]
- [[Residual Neural Network]]





- [[Deep Learning by Goodfellow]] pp 395 - 397