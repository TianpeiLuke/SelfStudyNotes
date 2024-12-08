---
tags:
  - concept
  - machine_learning/models
  - deep_learning/architecture
  - deep_learning/sequential_networks
  - deep_learning/models
keywords:
  - gru
  - gated_recurrent_neural_network
topics:
  - deep_learning/network_block
  - deep_learning/models
  - deep_learning/sequential_networks
name: Gated Recurrent Units in Neural Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gated Recurrent Units in Neural Network

![[Long-Short Term Memory Network or LSTM#^2f4537]]

- [[Long-Short Term Memory Network or LSTM]]

>[!important] Definition
>In **gated recurrent unit (GRU)**, we combine the role of long-term memory and short-term memory into one state vector $h$. It consists of the following components
>- **Update Gate**: similar to forget gate and input gate, the update gate simultaneously control the *forget behavior* and *update behavior* $$u^{(t)} =  \sigma\left(U^{u}x^{(t)} + W^{u}\,h^{(t-1)} + b^{u}\right)$$
>- **Reset Gate**: controls how much information from *short-term memory* is retrained when updating the *new input information* $$r^{(t)} =  \sigma\left(U^{r}x^{(t)} + W^{r}\,h^{(t-1)} + b^{r}\right)$$
>- **Conditioned Self-Loop Update** for **state** $h^{(t)}$  is $$h^{(t)} = u^{(t)} \odot h^{(t-1)} + \left(1 -u^{(t)}\right) \odot \sigma \left(U x^{(t)} + W\,[r^{(t)} \odot h^{(t-1)}] + b\right) $$
>	- The candidate for new information is partially controlled by the reset gate $$\hat{h}^{(t)} = \sigma \left(U x^{(t)} + W\,[r^{(t)} \odot h^{(t-1)}] + b\right)$$ 
>	- The *reset* and *update gates* can individually “**ignore**” parts of the *state vector* $C^{(t-1)}$.

- [[Strategies for Multiple Time Scales Sequential Network]]
- [[Hadamard Product of Matrices]]

>[!info]
>Compared to LSTM, we combine the role of *long-term memory* $C^{(t)}$ and *short-term memory* $h^{(t)}$ into **one state vector** $h^{(t)}$. 
>
>By self-loop updating, we can retain memory in $h^{(t)}$ as the long-term memory, and reset the memory in both *update gate* and *reset gate*.



## Explanation

>[!quote]
>Which pieces of the LSTM architecture are actually **necessary**? What other successful architectures could be designed that allow the network to **dynamically control the time scale** and **forgetting behavior** of different units?  
>
>Some answers to these questions are given with the recent work on gated RNNs, whose units are also known as **gated recurrent units**, or **GRUs** (Cho et al., 2014b; Chung et al., 2014, 2015a; Jozefowicz et al., 2015; Chrupala et al., 2015). The main *difference* with the LSTM is that a single gating unit *simultaneously* controls the *forgetting factor* and the decision to *update* the state unit.
>
>-- [[Deep Learning by Goodfellow]] pp 400

>[!quote]
>The **update gates** act like *conditional leaky integrators* that can linearly gate any dimension, thus choosing to *copy* it (at one extreme of the sigmoid) or *completely ignore* it (at the other extreme) by *replacing* it with the *new “target state” value* (toward which the leaky integrator wants to converge). The **reset gates** control which *parts* of the state get used to compute the *next target state*, introducing an additional *nonlinear* effect in the *relationship* between past state and future state.  
>
>-- [[Deep Learning by Goodfellow]] pp 401




-----------
##  Recommended Notes and References


- [[Long-Short Term Memory Network or LSTM]]
- [[Recurrent Neural Network]]
- [[Artificial Neural Network and Deep Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]] pp 382
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 636
- [[Deep Learning by Goodfellow]] pp 400