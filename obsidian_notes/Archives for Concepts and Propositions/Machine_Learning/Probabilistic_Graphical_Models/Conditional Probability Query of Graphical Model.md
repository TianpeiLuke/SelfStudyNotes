---
tags:
  - concept
  - machine_learning/strategy
  - probabilistic_graphical_models/theory
keywords:
  - probabilistic_graphical_model
  - conditional_probability
topics:
  - machine_learning_strategy
name: Conditional Probability Query of Graphical Model
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Conditional Probability Query of Graphical Model

>[!important] Definition
>The most common query type is the **probability query**. Such query consists of two parts
>- The **evidence**:  a subset of *variables* $E$ in the model and an *instantiation* $e$ to these variables;
>- the **query variables**: a subset $Y$ of random variables in the network
>  
>The task is to compute $$\mathcal{P}(Y | E = e),$$ that is, the **posterior distribution** over the value $y$ of $Y$, *conditioned on* the fact that $E = e$.  


## Explanation





-----------
##  Recommended Notes and References


- [[Sum-Product Variable Elimination]]
- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Belief-Update Expectation Propagation Algorithm]]


- [[Maximum A Posteriori Probability Query of Graphical Model]]
- [[Probabilistic Graphical Models]]



- [[Statistical Inference Problem]]


- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Graphical Models by Koller]] pp 26
- [[Deep Learning by Goodfellow]]