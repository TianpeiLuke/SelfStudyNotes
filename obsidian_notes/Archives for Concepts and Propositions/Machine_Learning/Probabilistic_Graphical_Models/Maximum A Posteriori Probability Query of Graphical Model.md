---
tags:
  - concept
  - machine_learning/strategy
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - maximum_a_posteriori_probability
  - probabilistic_graphical_model
topics:
  - machine_learning_strategy
name: Maximum A Posteriori Probability Query of Graphical Model
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Maximum A Posteriori Probability Query of Graphical Model

>[!important] Definition
>The **Maximum-A-Posteriori** (**MAP**) query (also called **most probable explanation (MPE)**), is the task of finding the most likely assignment to a set of variables $W$, given the *evidence* $E=e$, i.e. $$\text{MAP}(W | e) = \arg\max_{w}\mathcal{P}(w, e).$$


## Explanation

>[!quote]
>It is important to understand the difference between **MAP queries** and **probability queries**. In a MAP query, we are finding the *most likely* **joint assignment** to $W$. To find the most likely assignment to a single variable A, we could simply compute $\mathcal{P}(A | e)$ and then pick the most likely value. However, the assignment where each variable **individually picks** its *most likely value* can be quite **different** from the *most likely* **joint assignment** to all variables **simultaneously**. This phenomenon can occur even in the simplest case, where we have no evidence.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 26

- [[Conditional Probability Query of Graphical Model]]



-----------
##  Recommended Notes and References


- [[Complexity of Exact MAP Inference in Bayes Net]]


- [[Max-Product Variable Elimination]]
- [[Decoding Max-Marginal for Graphical Model]]
- [[Max-Product Belief Propagation for Clique Tree]]
- [[Max-Product Belief Update for Clique Tree]]

- [[Probabilistic Graphical Models]]

- [[Statistical Inference Problem]]

- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Graphical Models by Koller]]
- [[Deep Learning by Goodfellow]]