---
tags:
  - concept
  - deep_learning/sequential_networks
  - deep_learning/models
keywords:
  - back_propagation_algorithm
  - dynamic_bayesian_network
  - recurrent_neural_network
topics:
  - deep_learning/models
name: Back-Propagation Through Time
date of note: 2024-08-31
---

## Concept Definition

>[!important]
>**Name**: Back-Propagation Through Time

![[Back-Propagation Algorithm#^71c3c4]]

![[Back-Propagation Algorithm#^a79a3a]]

![[Back-Propagation Algorithm#^19b69f]]

- [[Automatic Differentiation]]
- [[Back-Propagation Algorithm]]

>[!important] Definition
>The **back-propagation through time (BPTT)** compute the gradient of loss function $L$ with respect to *parameters* *recursively through time.*
>
>For instance, consider the following RNN
>$$
>\begin{align*}
> a^{(t)} &= b + W\,h^{(t-1)} + U\,x^{(t)} \\[5pt]
> h^{(t)} &= \sigma \left(a^{(t)}\right) \\[5pt]
> o^{(t)} &= c + Vh^{(t)} \\[5pt]
> \hat{y}^{(t)} &= \text{softmax}(o^{(t)})  \\[5pt]
> L(\hat{y}^{(1:t)}, y^{(1 :t)}) &=  - \sum_{t}\,y^{(t)}\,\log \hat{y}_{t}
>\end{align*}
>$$
>
>The gradient of loss function $L$ with respect to parameters is 
>$$
>\begin{align*}
> \nabla_{c} L &= \sum_{t} \left(\frac{ \partial o^{(t)} }{ \partial c } \right)^{T}\,\nabla_{o^{(t)}}L \\[5pt]
> \nabla_{b} L &= \sum_{t} \left(\frac{ \partial h^{(t)} }{ \partial b } \right)^{T}\,\nabla_{h^{(t)}}L \\[5pt]
> \nabla_{V} L &= \sum_{t}\,\sum_{i}\left(\frac{ \partial L }{ \partial o_{i}^{(t)} } \right)\nabla_{V}\,o_{i}^{(t)} \\[5pt]
> \nabla_{W} L &= \sum_{t}\,\sum_{i}\left(\frac{ \partial L }{ \partial h_{i}^{(t)} } \right)\nabla_{W^{(t)}}\,h_{i}^{(t)} \\[5pt]
>\nabla_{U} L &= \sum_{t}\,\sum_{i}\left(\frac{ \partial L }{ \partial h_{i}^{(t)} } \right)\nabla_{U^{(t)}}\,h_{i}^{(t)} 
>\end{align*}
>$$

- [[Recurrent Neural Network]]
- [[Cross-Entropy Loss Function]]
- [[Dynamic Programming Algorithms]]


## Explanation





-----------
##  Recommended Notes and References


- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Back-Propagation Algorithm]]

- [[Recurrent Neural Network]]
- [[Automatic Differentiation]]


- [[Deep Learning by Goodfellow]] pp 374 - 376
- [[Deep Learning Foundations and Concepts by Bishop]] pp 381 - 382
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- [[Foundations of Computer Vision by Torralba]] 