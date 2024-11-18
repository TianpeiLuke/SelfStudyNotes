---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - residual_connection
  - residual_network
topics:
  - deep_learning/network_block
  - deep_learning/discriminative_models
  - deep_learning/sequential_networks
name: Residual Connection for Deep Learning
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Residual Connection for Deep Learning

### Vanishing Gradients and Exploding Gradients

![[Vanishing and Exploding Gradient Problems for Sequential Networks#^acbfbc]]

- [[Vanishing and Exploding Gradient Problems for Sequential Networks]]

### Residual Connection

>[!important] Definition
>The **residual connection** or **skip connection** is an important modification of network architecture that helps training *extremely deep network* ($>20$ layers)
>
>With *residual connection*, the output of each **residual block** contains an additive term *directly from* input, i.e.
>$$
>z = f(x; W) + x
>$$
>- The term **residual** comes from the fact that the residual block learns the *residual* between the *identity map* and the *desired output*. $$f(z^{(l-1)}; W^{(l)}) = z^{(l)} - z^{(l-1)}$$


^1c9b0f

![[residual_connections.png]]

### Residual Network

- [[Residual Neural Network]]


## Explanation

>[!quote]
>If we stack a *large number* of nonlinear layers together, the signal may get *squashed* to zero or may *blow up to infinity*, depending on the magnitude of the weights, and the nature of the nonlinearities. Similar problems can plague *gradients* that are passed backwards through the network (see Section 6.2).
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626

>[!quote]
>One way to obtain coarse time scales is to **add direct connections** from variables in the distant past to variables in the present. The idea of using such **skip connections** dates back to Lin et al. (1996) and follows from the idea of *incorporating delays* in feedforward neural networks (Lang and Hinton, 1988). In an ordinary recurrent network, a recurrent connection goes from a unit at time $t$ to a unit at time $t + 1$. It is possible to construct recurrent networks with longer delays (Bengio, 1991). 
>- Note that gradients may vanish or explode exponentially *with respect to* **the number of time steps**.
>- e.g. Lin et al. (1996) introduced recurrent connections with a **time delay** of $d$ to mitigate this problem.
>
>-- [[Deep Learning by Goodfellow]] pp 295

^259204

>[!quote]
>even with batch normalization, it becomes increasingly difficult to train networks with a large number of layers. 
>
>One explanation for this phenomenon is called **shattered gradients** (Balduzzi et al., 2017). 
>- We have seen that the representational capabilities of neural networks increase exponentially with depth. 
>- With ReLU activation functions, there is an *exponential increase* in the **number of linear regions** that the network can represent. 
>- However, a consequence of this is a **proliferation of discontinuities** in the gradient of the error function. 
>	- This is illustrated for networks with a single input variable and a single output variable in Figure 9.12. Here the derivative of the output variable with respect to the input variable (the Jacobian of the network) is plotted as a function of the input variable. 
>	- From the chain rule of calculus, these derivatives determine the *gradients of the error function surface*. 
>	- We see that for deep networks, **extremely small changes** in the *weight parameters* in the **early layers** of the network can produce *significant changes* in the gradient. 
>	- *Iterative gradient-based optimization algorithms* assume that the gradient **varies smoothly** across parameter space, and hence this ‘shattered gradient’ effect can render **training ineffective** in very deep networks
>
>![[shattered_gradient.png]]
>-- [[Deep Learning Foundations and Concepts by Bishop]]	 pp 274


## Neural ODE

![[Neural Ordinary Differential Equations#^b54270]]

- [[Neural Ordinary Differential Equations]]




-----------
##  Recommended Notes and References


- [[Residual Neural Network]]


- [[Deep Learning by Goodfellow]] pp 368
- [[Deep Learning Foundations and Concepts by Bishop]] pp 274 - 277
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626
- Torralba, A., Isola, P., & Freeman, W. T. (2024). _Foundations of Computer Vision_. The MIT Press.