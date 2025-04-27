---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - CRF
  - conditional_random_field
keywords:
  - CRF
  - conditional_random_field
topics:
  - probabilistic_graphical_model
name: Conditional Random Field
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Conditional Random Field

>[!important] Definition
>A **Conditional Random Field (CRF)** is a class of *probabilistic graphical models* used for structured prediction, where 
>- the goal is to model the conditional distribution $$p(\mathbf{y}|\mathbf{x})$$ of a set of output variables $\mathbf{y}$ given input variables $\mathbf{x}$, 
>- while capturing dependencies between output variables explicitly.

- [[Markov Network on Undirected Graph]]


### Model Formulation

>[!important] Model Formulation
>Given:
>- An input sequence $\mathbf{x} = (x_1, x_2, \ldots, x_n)$
>- A corresponding output sequence $\mathbf{y} = (y_1, y_2, \ldots, y_n)$
>
>A **linear-chain CRF** defines the conditional probability as:
>$$
>p(\mathbf{y} \mid \mathbf{x}) = \frac{1}{Z(\mathbf{x})} \exp\left( \sum_{t=1}^n \sum_{k} w_k \, f_k(y_{t-1}, y_t, \mathbf{x}, t) \right)
>$$
>where:
>- $f_k$ are **feature functions** depending on the current and previous labels, the input, and the position $t$.
>- $w_k$ are **model parameters** (weights).
>- $Z(\mathbf{x})$ is the **partition function** (normalization constant):
>  $$
>  Z(\mathbf{x}) = \sum_{\mathbf{y}} \exp\left( \sum_{t=1}^n \sum_{k} w_k \, f_k(y_{t-1}, y_t, \mathbf{x}, t) \right).
>  $$

^88974e

- [[Exponential Family of Distributions]]
- [[Log-Partition Function and Score Function of Graphical Models]]

### Inference Algorithm

>[!important] Inference Algorithm
>Inference in CRFs involves two major tasks:
>
>- **Decoding**: Finding the most likely output sequence (MAP estimate):
>  $$
>  \hat{\mathbf{y}} = \arg\max_{\mathbf{y}} p(\mathbf{y} \mid \mathbf{x})
>  $$
>  This can be efficiently solved using the **Viterbi algorithm**, a dynamic programming method analogous to decoding in Hidden Markov Models.
>
>- **Marginal Inference**: Computing marginal probabilities $p(y_t \mid \mathbf{x})$ or $p(y_t, y_{t-1} \mid \mathbf{x})$.
>  - This can be done using the **forward-backward algorithm**, a dynamic programming procedure.

- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]

#### Viterbi Algorithm

- [[CRF MAP Inference via Viterbi Algorithm]]


### Learning Algorithm

>[!important] Learning Algorithm
>Learning in CRFs is typically performed by **maximum conditional likelihood estimation**:
>
>- Objective function (negative log-likelihood):
>  $$
>  \mathcal{L}(w) = -\sum_{i=1}^N \log p(\mathbf{y}^{(i)} \mid \mathbf{x}^{(i)}; w)
>  $$
>  where $(\mathbf{x}^{(i)}, \mathbf{y}^{(i)})$ are training examples.
>
>- Gradient of the objective:
>  $$
>  \nabla_w \mathcal{L}(w) = \mathbb{E}_{p(\mathbf{y} \mid \mathbf{x})}[\mathbf{f}] - \mathbf{f}(\mathbf{y}^{(i)}, \mathbf{x}^{(i)})
>  $$
>  where $\mathbf{f}$ is the vector of feature functions aggregated over the sequence.


>[!important]
>Optimization methods:
>  - **Gradient-based methods** (e.g., L-BFGS)
>  - **Stochastic gradient descent (SGD)** for large-scale datasets
>
>- Computing the gradient requires **marginal inference** (using forward-backward).
>
>- **Regularization** (e.g., $L_2$ penalty) is often added to prevent overfitting.

- [[Stochastic Gradient Descent Algorithm]]
- [[Limited Memory BFGS]]



## Explanation

>[!info]
>- **CRFs** are *undirected graphical models* (Markov random fields) globally conditioned on the observed input $\mathbf{x}$.
>- They are widely used in *sequence labeling*, .e.g 
>	- part-of-speech tagging, 
>	- named entity recognition 
>	- and general *structured output problems*.


- [[Markov Network on Undirected Graph]]
- [[Sequence Labeling Task]]
- [[Part-of-Speech Tagging]]
- [[Name Entity Recognition]]

>[!info]
>**Linear-chain CRFs** are for sequences; **general CRFs** can model arbitrary graph structures (e.g., image segmentation with grid CRFs).

>[!info]
>Unlike generative models (like **HMMs**), CRFs directly model $$p(\mathbf{y}|\mathbf{x})$$ without needing to model $p(\mathbf{x})$.




-----------
##  Recommended Notes and References





- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Elements of Statistical Learning by Hastie]]
- [[Speech and Language Processing by Jurafsky]] pp 376