---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - deep_learning/models
  - deep_learning/architecture
keywords:
  - mlp
  - multilayer_perceptron
  - fully_connected_network
topics:
  - deep_learning/algorithm
  - deep_learning/network_block
name: Multi-Layer Perceptron and Fully Connected Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Multi-Layer Perceptron and Fully Connected Network

>[!important] Definition
>The quintessential deep learning models are the **feedforward neural networks**, or **multilayer perceptrons (MLPs)**. 
>
>A **feedforward network** defines a mapping $$y = f(x; \theta)$$ where the goal is find $\theta^{*}$ that best *approximate* $y=f^{*}(x)$.
>- These models are called *feedforward* because information flows through the function being evaluated from $x$, through the *intermediate* computations used to define $f$, and finally to the output $y$.
>- There are *no feedback connections* in which outputs of the model are fed back into itself.

- [[Logistic Regression]]
- [[Perceptron Algorithm]]

![[feedforward_nn.png]]


>[!important] Definition
>A **feedforward network** is represented by *composition of multiple functions*, e.g. $$f(x) := f^{(3)}(f^{(2)}(f^{(1)}(x))) $$
>
>These *chain structures* are the most commonly used structures of neural networks.
>- From **input to output**, the first function $f^{(1)}$ is called the **first layer**; the second function $f^{(2)}$ is called the *second layer*
>- The overall *length* of the chain is called the **depth** of the model.
>- The final layer is called the **output layer**.
>- The layers that do not directly take input from training data are called the **hidden layers**.
>- Each hidden layer of the network is typically *vector valued*. The *dimensionality* of these hidden layers determines the **width** of the model.
>- Each *element* of the vector may be interpreted as playing a role analogous to a **neuron**.
>- Instead of representing layers are *vector-to-vector function*, we can also think of the layer as consisting of many **units** that act *in parallel*, each representing a *vector-to-scalar function*.
>  


>[!important] Definition
>In **MLP**, each layer $i$ is represented by a composite of *linear function* and a *non-linear activation function* $$x^{(i+1)} = f^{(i)}(x^{(i)}) = \sigma \left((W^{(i)})^{T}x^{(i)} + b^{(i)} \right)$$
>- assume that $x^{(i)} \in \mathbb{R}^{d_{i}}$, and $x^{(i+1)}  \in \mathbb{R}^{d_{i+1}}$
>- $W^{(i)} \in \mathbb{R}^{d_{i} \times d_{i+1}}$ is the **weight matrix** for layer $i$, and $b^{(i)}\in \mathbb{R}^{d_{i+1}}$ is the **bias term**
>- $\sigma(x)$ is the **activation function**
>- we call the input of activation function as **pre-activation** $$a = (W^{(i)})^{T}x^{(i)} + b^{(i)}$$
>
>Each *unit* $j$ of layer $i+1$ is given by 
>$$
>\begin{align*}
>x_{j}^{(i+1)} &= \sigma \left((W_{j}^{(i)})^{T}x^{(i)} + b_{j}^{(i)}\right)\\[5pt]
>&= \sigma \left(\sum_{k=1}^{d_{i}}W_{kj}^{(i)}\,x_{k}^{(i)} + b_{j}^{(i)}\right), \quad j=1\,{,}\ldots{,}\,d_{i+1} 
>\end{align*}
>$$
>
>![[nn_diagram.png]]  

- [[Activation Functions for Deep Learning]]


## Explanation





-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]
- [[Perceptron Algorithm]]
- [[Logistic Regression]]

- [[Back-Propagation Algorithm]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 180
- [[Deep Learning by Goodfellow]]  pp 163 - 191
- [[Deep Learning Foundations and Concepts by Bishop]] pp 17
- Wikipedia [Multilayer_perceptron](https://en.wikipedia.org/wiki/Multilayer_perceptron)