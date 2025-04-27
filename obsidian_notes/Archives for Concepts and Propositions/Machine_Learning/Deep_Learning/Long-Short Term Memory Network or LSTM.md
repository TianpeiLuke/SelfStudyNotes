---
tags:
  - concept
  - machine_learning/models
  - deep_learning/sequential_networks
  - deep_learning/models
  - deep_learning/architecture
  - LSTM
  - lstm_network
  - long-term_memory
  - short-term_memory
  - long_short_term_memory
keywords:
  - lstm_network
  - long_short_term_memory
  - long-term memory
  - short-term memory
topics:
  - deep_learning/models
  - deep_learning/network_block
name: Long-Short Term Memory Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Long-Short Term Memory Network

>[!quote]
>the most effective sequence models used in practical applications are called **gated RNNs** . These include the **long short-term memory** and networks based on the **gated recurrent unit**.
>
>Like *leaky units*, *gated RNNs* are based on the **idea** of creating **paths through time** that have derivatives that *neither vanish nor explode*. Leaky units did this with connection weights that were either manually chosen constants or were parameters. Gated RNNs generalize this to *connection weights* that may *change at each time step*.  
>
>Leaky units allow the network to **accumulate information** (such as evidence for a particular feature or category) over a long duration. Once that information has been used, however, it might be useful for the neural network to **forget the old state**. For example, if a sequence is made of subsequences and we want a leaky unit to accumulate evidence inside each sub-subsequence, we need a mechanism to forget the old state by setting it to zero. Instead of manually deciding when to clear the state, we want the neural network to *learn to decide when to do it*. This is what gated RNNs do.
>
>-- [[Deep Learning by Goodfellow]] pp 397

- [[Recurrent Neural Network]]
- [[Gated Recurrent Units in Neural Network]]

>[!important] Definition
>A **long short-term memory (LSTM) cell** is described by the following components
>- *Require*: **context units** or **state units** i.e. the **long-term memory** $C^{(t-1)}$
>- *Require*: **hidden units**, i.e. the **short-term memory** $h^{(t-1)}$
>- **Forget Gate**: the state units have a **linear self-loop** whose *weight* is controlled by a *forget gate unit*: $$f^{(t)} = \sigma \left(U^{f}x^{(t)} + W^{f}\,h^{(t-1)} + b^{f}\right)$$ where $x^{(t)}$ is the input of network at time $t$
>	- The role of forget gate is to control how much information from *memory* to *retain* in *long term*
>	- $$(U^{f}, W^{f}, b^{f})$$ are additional learnable parameters for forget gate.
>- **Input Gate**: controls how much information from *input* to remember in *long term* $$i^{(t)} = \sigma \left(U^{i}x^{(t)} + W^{i}\,h^{(t-1)} + b^{i}\right)$$
>	- $$(U^{i}, W^{i}, b^{i})$$ are additional learnable parameters for input gate.
>- **Conditional Self-Loop Update** for *state units/long term memory* are given by $$C^{(t)} = f^{(t)} \odot C^{(t-1)} + i^{(t)} \odot \sigma \left(U x^{(t)} + W\,h^{(t-1)} + b\right) $$
>	- The update of *long-term memory* is controlled by two gates: 
>		- *forget gate* controls the flow of *previous information*
>		- *input gate* controls the flow of *new information*
>	- Note that $$\hat{C}^{(t)} = \sigma \left(U x^{(t)} + W\,h^{(t-1)} + b\right)$$ define the new information into the cell.
>	- $\hat{C}^{(t)}$ is called the **candidate gate** in some literature, and $\sigma(\cdot) := \tanh(\cdot)$ for candidate gate.
>- **Output Gate**: controls the output of *short-term memory* $$o^{(t)} = \sigma\left(U^{o}x^{(t)} + W^{o}\,h^{(t-1)} + b^{o}\right)$$
>- **Update** of **short-term memory** via activation of long-term memory, controlled by output gate $$h^{(t)} = o^{(t)} \odot \tanh(C^{(t)})$$
>	- Note that the *short-term memory* is the output of *sigmoid activation* via *long-term memory* 
>- *Output*: the state vector $C^{(t)}$ and hidden vector $h^{(t)}$ at next time

^2f4537


- [[Rectified Linear Unit as Activation for Deep Learning]]
- [[Sigmoid Function as Activation for Deep Learning]]
- [[Strategies for Multiple Time Scales Sequential Network]]
- [[Hadamard Product of Matrices]]


![[lstm.png]]



## Explanation

>[!quote]
>The clever idea of introducing **self-loops** to produce paths where the *gradient* can *flow* for long durations is a **core contribution** of the initial *long short-term memory (LSTM) model*. A crucial addition has been to make the *weight* on this *self-loop* **conditioned on the context**, rather than fixed (Gers et al., 2000). By making the weight of this *self-loop gated* (controlled by *another hidden unit*), the time scale of integration can be changed *dynamically*. In this case, we mean that even for an LSTM with fixed parameters, the **time scale of integration** can *change* based on the *input sequence*, because the time constants are output by the model itself.
>
>-- [[Deep Learning by Goodfellow]] pp 397

>[!quote]
>Instead of a unit that simply applies an element-wise nonlinearity to the affine transformation of inputs and recurrent units, *LSTM recurrent networks* have “**LSTM cells**” that have an **internal recurrence** (a *self-loop*), in addition to the **outer recurrence** of the RNN. Each cell has the same inputs and outputs as an ordinary recurrent network, but also has more parameters and *a system of gating units* that controls the flow of information.
>
>-- [[Deep Learning by Goodfellow]] pp 399





-----------
##  Recommended Notes and References

- [[Recurrent Neural Network]]
- [[Vanishing and Exploding Gradient Problems for Sequential Networks]]

- [[Dynamic Bayesian Network]]
- [[State-Observation Models]]
- [[Hidden Markov Model]]
- [[Linear Dynamic System]]
- [[Artificial Neural Network and Deep Learning]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 382
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 636
- [[Deep Learning by Goodfellow]] pp 297, 397 - 399, 413
- Medium [long-short-term-memory-lstm](https://medium.com/@saba99/long-short-term-memory-lstm-fffc5eaebfdc)