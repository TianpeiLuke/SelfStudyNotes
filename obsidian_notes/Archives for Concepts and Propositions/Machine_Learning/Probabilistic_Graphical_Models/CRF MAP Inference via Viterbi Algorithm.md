---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - CRF
  - conditional_random_field
  - viterbi_decoding
  - viterbi_algorithm
keywords:
  - CRF
  - conditional_random_field
topics:
  - probabilistic_graphical_model
name: Conditional Random Field MAP Inference via Viterbi Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: CRF MAP Inference via Viterbi Algorithm

### Model Formulation

![[Conditional Random Field#^88974e]]

- [[Conditional Random Field]]
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

### Viterbi Algorithm

>[!important] Definition
>The **Viterbi algorithm** is a *dynamic programming* method used in Conditional Random Fields (CRFs) to efficiently compute the most likely sequence of labels (the MAP estimate) given an observed input sequence.
>
>- *Require*: input sequence $\mathbf{x} = (x_1, \ldots, x_n)$
>- *Require*: model parameters $\{w_k\}$ and feature functions $\{f_k(y_{t-1}, y_t, \mathbf{x}, t)\}$
>
>- The goal is to compute:
>  $$
>  \hat{\mathbf{y}} = \arg\max_{\mathbf{y}} p(\mathbf{y} \mid \mathbf{x}).
>  $$
>  In a linear-chain CRF, this reduces to finding the sequence $\mathbf{y}$ maximizing the *sum* of **local scores**:
>  $$
>  \sum_{t=1}^n \sum_{k} w_k \, f_k(y_{t-1}, y_t, \mathbf{x}, t).
>  $$
>
>- **Initialize**:
>    - For each label $y_1$:
>      $$
>      \delta_1(y_1) = \sum_{k} w_k \, f_k(\text{START}, y_1, \mathbf{x}, 1)
>      $$
>    - Set backpointer $\psi_1(y_1) = \text{NULL}$.
>
>- For $t = 2, \ldots, n$:
>    - For each possible label $y_t$:
>      $$
>      \delta_t(y_t) = \max_{y_{t-1}} \left[ \delta_{t-1}(y_{t-1}) + \sum_{k} w_k \, f_k(y_{t-1}, y_t, \mathbf{x}, t) \right]
>      $$
>    - Record the best previous label:
>      $$
>      \psi_t(y_t) = \arg\max_{y_{t-1}} \left[ \delta_{t-1}(y_{t-1}) + \sum_{k} w_k \, f_k(y_{t-1}, y_t, \mathbf{x}, t) \right].
>      $$
>
>- **Termination**:
>    - Find the final best label:
>      $$
>      \hat{y}_n = \arg\max_{y_n} \delta_n(y_n).
>      $$
>
>- **Backtracking**:
>    - For $t = n-1, n-2, \ldots, 1$:
>      $$
>      \hat{y}_t = \psi_{t+1}(\hat{y}_{t+1}).
>      $$
>
>- *Return*: the most likely sequence $$\hat{\mathbf{y}} = (\hat{y}_1, \hat{y}_2, \ldots, \hat{y}_n).$$

- [[Dynamic Programming Algorithms]]



## Explanation




-----------
##  Recommended Notes and References





- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Elements of Statistical Learning by Hastie]]
- [[Speech and Language Processing by Jurafsky]] pp 376