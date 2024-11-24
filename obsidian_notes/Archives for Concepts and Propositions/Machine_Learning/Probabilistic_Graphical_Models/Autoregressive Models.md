---
tags:
  - concept
  - statistics/estimation
  - statistics/inference
  - deep_learning/generative_models
  - probabilistic_graphical_models/models
keywords:
  - autoregressive_model
topics:
  - probabilistic_graphical_model
  - deep_learning/generative_models
  - statistics/inference
name: Autoregressive Models
date of note: 2024-11-14
---

## Concept Definition

>[!important]
>**Name**: Autoregressive Models

![[Bayesian Network on Directed Acyclic Graph#^9d991d]]

>[!important] Definition
>A fully connected *directed acyclic graph (DAG)* $(\mathcal{G}, P)$ is called an **autoregressive model (ARM)** if its joint distribution factorizes as follows:
>$$
>p(x_{1}\,{,}\ldots{,}\,x_{T}) = \prod_{t=1}^{T}\,p(x_{t}\,|\,x_{1:t-1})
>$$
>- This corresponds to a fully connected DAG, in which each node depends on *all its predecessors* in the ordering.

- [[Bayesian Network on Directed Acyclic Graph]]
- [[n-Gram Model and Language Model]]

![[autoregressive_model.png]]
## Explanation

>[!quote]
>Although the decomposition in Equation 
>$$
>p(x_{1}\,{,}\ldots{,}\,x_{T}) = \prod_{t=1}^{T}\,p(x_{t}\,|\,x_{1:t-1})
>$$
>is general, each term in this expression (i.e., each conditional distribution $p(x_{t}|x_{1:t-1})$) becomes **more and more complex**, since it depends on an increasing number of arguments, which makes the terms slow to compute, and makes estimating their parameters **more data hungry**.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 811

>[!info]
>One of major **drawbacks** is that the *inference* of **autoregressive model** can only be **sequential**, making it time-consuming.


## Applications

### Markov Model

>[!quote]
>One approach to solve the intractability of autoregressive model is to make the **Markov assumption** i.e. $$p(x_{t}\,|\,x_{1:t-1}) = p(x_{t}\,|\,x_{t-1})$$
>- This is called the **autoregressive model** of **order 1.**
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 811  

- [[Markov Chain and Markov Process]]

![[Autoregressive Time Series#^36ea9a]]

- [[Autoregressive Time Series]]

![[n-Gram Model and Language Model#^b7a2b4]]

- [[n-Gram Model and Language Model]]


### Relaxation with Hidden States

>[!important]
>Unfortunately, the Markov assumption is very limiting. 
>
>One way to **relax** it, and to make $x_{t}$ depend on all the past $x_{1: t-1}$ **without explicitly regressing** on them, is to assume the past can be compressed into a *hidden state* $z_{t}$.

#### State Space Model and Dynamic System

![[State Space Models and Nonlinear Dynamic System#^4beaac]]

- [[State-Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]

#### Linear Dynamic System

- [[Linear Dynamic System]]
- [[Kalman Filter Discrete-Time]]

####  Dynamic Bayesian Network

- [[Dynamic Bayesian Network]]

![[Hidden Markov Model#^f3f54e]]

- [[Hidden Markov Model]]

#### Recurrent Neural Network

![[Recurrent Neural Network#^81c4ad]]

- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network]]
- [[Gated Recurrent Units in Neural Network]]
- [[Encoder-Decoder Sequence-to-Sequence Architecture]]


### Restricting Conditional Functionals

>[!quote]
>Another approach is to stay with the *general AR model* of Equation,
>$$
>p(x_{1}\,{,}\ldots{,}\,x_{T}) = \prod_{t=1}^{T}\,p(x_{t}\,|\,x_{1:t-1})
>$$
> but to use a **restricted functional form**, such as some kind of neural network, for the conditionals $p(x_{t}\,|\,x_{1:t-1})$. 
> 
> Thus rather than making conditional independence assumptions, or explicitly compressing the past into a sufficient statistic, we implicitly *learn a compact mapping* from the past to the future.
> 
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 811 

#### Causal CNN

- [[Causal Convolutional Neural Network]]

#### Normalizing Flow

- [[Normalizing Flows]]
- [[Autoregressive Flows]]

#### Diffusion Network

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


#### Transformer Network

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Generative Pre-trained Transformer or GPT]]





-----------
##  Recommended Notes and References



- [[Deep Learning Foundations and Concepts by Bishop]] pp 350, 379
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 811 - 813