---
tags:
  - concept
  - deep_learning/models
  - deep_learning/sequential_networks
keywords:
  - vanishing_gradient
  - exploding_gradient
topics:
  - deep_learning/sequential_networks
name: Vanishing and Exploding Gradient Problems for Sequential Networks
date of note: 2024-09-02
---

## Concept Definition

>[!important]
>**Name**: Vanishing and Exploding Gradient Problems for Sequential Networks

### Challenge of Learning Long-Term Dependencies 

>[!important]
>The mathematical challenge of learning **long-term dependencies** in recurrent networks can be summaried as the following problems. 
>
>- The **vanishing** and **exploding gradient**.  
>	- That is, the **gradients** propagated over *many stages* tend to either **vanish** (most of the time) or **explode** (rarely, but with much damage to the optimization).
>- The **exponentially smaller weights** given to *long-term interactions* compared to the *short-term* one.

^1610ad

- [[Recurrent Neural Network]]
- [[Strategies for Multiple Time Scales Sequential Network]]

### Vanishing and Exploding Gradient Problem

>[!important] Definition
>The **vanishing** and **exploding gradient** of recurrent network comes from the *multiplication of weight matrices* over many stages.
>
>Consider a simplified example of recurrent unit with linear activation $$h^{(t)} = W^{T}\,h^{(t-1)}$$
>- It can be seen as the **power iteration** and the $t$-step state depends on the initial state as $$h^{(t)} = (W^{t})^{T}\,h^{(0)}$$
>- Assume that $W$ is self-adjoint, and the *spectral decomposition* of $W$ is given by $$W = U\Lambda U^{T}$$
>- Thus the power iteration of state equation becomes $$h^{(t)} = U^{T}\,\Lambda^{t}\, U\,h^{(0)}$$
>	- The eigenvalue of the power-scaled weight grow *exponentially large or small* $$t\to \infty \implies \lambda_{i}^{t} \to \left\{\begin{array}{cl} 0 &\text{ if } |\lambda_{i}| < 1 \\[5pt] \infty &\text{ if } |\lambda_{i}| > 1\end{array}\right.$$

^acbfbc

- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


## Explanation

>[!quote]
>One may hope that the problem can be avoided simply by **staying in a region of parameter space** where the gradients do not vanish or explode. 
>- Unfortunately, in order to **store memories** in a way that is *robust to small perturbations*, the RNN must enter a region of parameter space where *gradients vanish* (Bengio et al., 1993, 1994). 
>- Specifically, whenever the model is able to represent **long-term dependencies**, the **gradient of a long-term interaction** has *exponentially smaller magnitude* than the gradient of a short-term interaction. 
>- This means not that it is impossible to learn, but that it might take a **very long time** to learn *long-term dependencies*, because the signal about these dependencies will tend to be **hidden by the smallest fluctuations** arising from *short-term dependencies*. 
>- In practice, the experiments in Bengio et al. (1994) show that as we increase the span of the dependencies that need to be captured, gradient-based optimization becomes increasingly difficult, with the probability of successful training of a traditional RNN via SGD rapidly reaching $0$ for sequences of only length $10$ or $20$.
>  
>-- [[Deep Learning by Goodfellow]] pp 392



## Techniques that Mitigate the Vanishing and Exploding Gradient Issue


### Leaky Activations

- [[Rectified Linear Unit as Activation for Deep Learning]]

### Batch Normalization

- [[Batch Normalization]]
- [[Layer Normalization]]

### Gradient Clip



### Residual Connections

- [[Residual Neural Network]]
- [[Residual Connection for Deep Learning]]

### Self-Attention Mechanism

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]







-----------
##  Recommended Notes and References



- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network]]








- [[Deep Learning by Goodfellow]] pp 390 - 392
- [[Deep Learning Foundations and Concepts by Bishop]] pp 382
