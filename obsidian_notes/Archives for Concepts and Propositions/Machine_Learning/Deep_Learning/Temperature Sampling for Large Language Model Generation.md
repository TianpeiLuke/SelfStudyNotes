---
tags:
  - concept
  - deep_learning/generative_models
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords: 
topics: 
name: 
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Temperature Sampling for Large Language Model Generation

![[Greedy Decoding for Causal Language Model Generation#^41dfb7]]

- [[Greedy Decoding for Causal Language Model Generation]]

>[!important] Defiinition
>In **temperature sampling**, instead of truncating the distribution, we reshape it.
>
>- The it  assumes that the *paremeterized distribution* over word $w_{i}\in \mathcal{V}$ is given by the *soft-max function*
>$$
>p_{i} = \text{soft-max}(u_{i}) := \frac{e^{u_{i}}}{\sum_{j=1}^{k}e^{u_{j}}}, \quad i=1\,{,}\ldots{,}\,|\mathcal{V}|
>$$
>where $u_{i}$ is the output last layer of model $$u_{i} = \left\langle  h\,,\,E(w_{i})    \right\rangle$$ and $E$ is the *contextualized embedding* from lower-level neural network.
>
>Specifically, the **temperature sampling** rescales the logit function of language model by a **temperature parameter** $T>0$, i.e.  
>$$
>p_{i} = \text{soft-max}(u_{i} / T) := \frac{ \exp\left(u_{i} / T\right)}{\sum_{j=1}^{k}\exp\left(u_{j} / T\right)}, \quad i=1\,{,}\ldots{,}\,|\mathcal{V}|
>$$
>where 
>- $T \to 1$, the distribution close to uniform
>- $T \to 0$, the distribution *close to* $\arg\max$ $$T\to 0\implies \text{soft-max}\left( \frac{u}{T} \right) \to \arg\max(u)$$

- [[Multinomial Distribution]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Decoding and Sampling from Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]

![[langugage_model_head.png]]

## Explanation


>[!info]
>The **temperature sampling** is a *soft-version* of **top-k sampling.**

- [[Top-k Sampling for Large Language Model Generation]]

>[!info]
>**Softmax** as parameterized distribution function for discrete categorical values is widely used.
>
>For instance
>- **policy gradient method** [[Policy Gradient Algorithm]]
>- **multinomial regression** [[Generalized Linear Models]]

>[!info]
>*Reshaping* the distribution by **temperature factor** is the key for stochastic optimization such as
>-  [[Simulated Annealing]]
>- [[Annealed Importance Sampling]]

>[!info]
>The **temperature-based sampling** uses the **energy-based models**

- [[Gibbs Measure and Energy-based Model]]


-----------
##  Recommended Notes and References


- [[Simulated Annealing]]
- [[Gibbs Sampling for Graphical Model]]
- [[Artificial Neural Network and Deep Learning]]
- [[Generative Pre-trained Transformer or GPT]]

- [[Speech and Language Processing by Jurafsky]] pp 208
- [[Deep Learning Foundations and Concepts by Bishop]] pp 386 - 387
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]