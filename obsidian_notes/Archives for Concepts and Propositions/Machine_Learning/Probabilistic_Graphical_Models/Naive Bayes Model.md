---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - naive_bayes_model
  - naive_bayes_classifier
keywords:
  - naive_bayes_model
  - naive_bayes_classifier
topics:
  - probabilistic_graphical_model
  - machine_learning_models
name: Naive Bayes Model
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Naive Bayes Model

>[!important] Definition
>Let $(X_{1}\,{,}\ldots{,}\,X_{D}, Y)$ be random sample from $\mathcal{X}^{D}\times \mathcal{Y}$.
>
>The **naive Bayes model** assumes that given response $Y$, all covariates $X_{1}\,{,}\ldots{,}\,X_{D}$ are *conditionally independent* i.e.
>$$
>p(X_{1}\,{,}\ldots{,}\,X_{D}\;|\;Y) = \prod_{i=1}^{D}\,p(X_{i}\;|\;Y)
>$$
>- By *Bayes theorem*, the **posterior distribution** of $Y$ given all covariates $X_{1}\,{,}\ldots{,}\,X_{D}$ is given by $$p(Y|\;X_{1}\,{,}\ldots{,}\,X_{D}) \propto p(Y)\; \prod_{i=1}^{D}\,p(X_{i}\;|\;Y)$$

- [[Conditional Independence]]
- [[Bayes Theorem]]

![[naive_bayes_1.png]]

### Multinomial Naive Bayes Algorithm

![[Multinomial Naive Bayes Model#^b4ddab]]

- [[Multinomial Naive Bayes Model]]

## Explanation

>[!info]
>**Naive Bayes model** is one of simplest **Bayesian network** with *star-spaced graph.*

- [[Bayesian Network on Directed Acyclic Graph]]

![[tree_naive_bayes.png]]




-----------
##  Recommended Notes and References




- [[Classification Problem]]
- [[Probabilistic Graphical Models]]


- [[Speech and Language Processing by Jurafsky]] pp 57 - 61
- [[Probabilistic Graphical Models by Koller]] pp 47, 727, 767, 875 - 877
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 164
- [[Elements of Statistical Learning by Hastie]] pp 108, 210-211, 694
- [[Deep Learning Foundations and Concepts by Bishop]] pp 344, 378
- [[Deep Learning by Goodfellow]] pp 3