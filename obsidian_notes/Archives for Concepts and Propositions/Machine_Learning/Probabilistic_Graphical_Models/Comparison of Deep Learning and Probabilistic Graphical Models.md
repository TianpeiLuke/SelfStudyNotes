---
tags:
  - thought
  - probabilistic_graphical_models
  - deep_learning
  - comparison
keywords:
  - deep_learning
  - probabilistic_graphical_model
topics:
  - deep_learning
  - probabilistic_graphical_model
name: Comparison of Deep Learning and Probabilistic Graphical Models
date of note: 2025-05-07
---

## Concept Definition

>[!important]
>**Name**: Comparison of Deep Learning and Probabilistic Graphical Models

### Comparison

| Dimension                          | **Deep Learning (DL)**                                                                                                                                                       | **Probabilistic Graphical Models (PGMs)**                                                                                                                                     |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Core abstraction**               | Layers of **differentiable functions** (neural networks) that learn hierarchical **representations** from data.                                                              | **Graph structure** (directed → Bayesian networks, undirected → Markov networks) that encodes **conditional independencies** and factorises a joint probability distribution. |
| **Primary goal**                   | - **Predict** (or generate) by optimising a task-specific loss via gradient descent; <br>- uncertainty is optional.                                                          | - Model the full *joint distribution* $$p(X,Z,\dots)$$ for _inference_ (marginals, conditionals) and _learning_; uncertainty is explicit.                                     |
| **Learning paradigm**              | - Mostly **discriminative**; <br>- back-prop + SGD. <br>- *Large-scale* data and compute.                                                                                    | - Both _generative_ and *discriminative*; <br>- *maximum likelihood*, <br>- EM, <br>- variational/BP, <br>- MCMC. <br>- Can work with *smaller* data if structure correct.    |
| **Uncertainty & interpretability** | - *Confidence* often ad-hoc (softmax, MC-Dropout, deep ensembles). <br>- Internal features are *hard to interpret*.                                                          | Probabilistic semantics give <br>- *calibrated uncertainty*, <br>- clear *causal/query interpretation*.                                                                       |
| **Data efficiency**                | - **High capacity** → needs lots of labelled data; <br>- pre-training and transfer mitigate this.                                                                            | - *Structural priors* and *parameter sharing* give good sample efficiency when graph *matches reality*.                                                                       |
| **Scalability**                    | - Scales to *billions* of samples and parameters with GPUs/TPUs; <br>- automatic differentiation.                                                                            | - Exact inference *NP-hard* in general; <br>- relies on sparsity or approximate (loopy BP, variational, sampling). <br>- Large dense graphs are *costly*.                     |
| **Expressiveness**                 | **Universal function approximators**; excels at images, speech, text, complex dynamics.                                                                                      | Expresses **causal relations**, missing-data mechanisms, heterogeneous variable types.                                                                                        |
| **Typical outputs**                | - *Point predictions*, <br>- *embeddings*, <br>- *generative samples* (diffusion, GAN, autoregressive).                                                                      | - *Posterior* *distributions*, <br>- *marginal* probabilities, <br>- most-probable explanations (*MAP*).                                                                      |
| **Handling missing data**          | Requires imputation or special architectures.                                                                                                                                | Built-in marginalisation handles missingness naturally.                                                                                                                       |
| **Causal reasoning**               | Not inherent; needs explicit design or counterfactual training.                                                                                                              | **Causal DAGs** enable do-calculus, intervention queries.                                                                                                                     |
| **Hybrid trends**                  | -  Probabilistic Deep Learning (**Bayesian NN**, **VAE**, **diffusion**).  <br>-  **Energy-based** models & neural Samplers.   <br>- Diffusion with latent PGMs (e.g., ADM). | - **Neural parameterisation** of factors (neural BP, neural variational inference).  <br>- **Amortised inference** (VAE-style) in complex PGMs.                               |
| **When to favour**                 | **Vision**, **NLP**, **RL**, pattern recognition with *massive data* and *weak domain priors*.                                                                               | Structured domains with **rich prior** knowledge, *missing data*, explicit uncertainty or *causal questions*.                                                                 |

- [[Probabilistic Graphical Models]]
- [[Artificial Neural Network and Deep Learning]]

- [[Deep Belief Network or DBN]]
- [[Bayesian Network on Directed Acyclic Graph]]

- [[Markov Network on Undirected Graph]]
- [[Restricted Boltzmann Machine or RBM]]

## Explanation


### Key Take-aways

>[!important]
> - **Deep learning** gives unmatched representational power and scale, but treats uncertainty as an add-on and is data-hungry.
>     
> - **PGMs** encode domain structure and yield principled probabilistic inference, but struggle with large-scale high-dimensional data and can be computationally heavy.
>     

### Causal Graphical Model

- [[D-Separation in Bayesian Network]]
- [[Causal Graph]]
- [[Structural Causal Models or SCMs]]
- [[do-Calculus]]


### Hybrid Methods

>[!info]
> Modern practice increasingly **combines both**: neural networks supply flexible factors or likelihoods, while variational inference or message-passing preserves probabilistic semantics—yielding models such as 
>- **variational auto-encoders**, 
>- **neural ODE PGMs**, 
>- or **deep Bayesian networks**.
> 

- [[Bayesian Neural Network]]
- [[Variational Auto-Encoder or VAE]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

- [[Gibbs Measure and Energy-based Model]]

- [[Neural Ordinary Differential Equations]]




-----------
##  Recommended Notes and References


- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Graphical Models by Koller]]
- [[Causality Models Reasoning and Inference by Pearl]]

