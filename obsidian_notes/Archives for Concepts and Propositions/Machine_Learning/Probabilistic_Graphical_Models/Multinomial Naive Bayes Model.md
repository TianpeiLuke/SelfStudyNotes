---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - natural_language_processing/topic_models
keywords:
  - naive_bayes_model
  - multinomial_distribution
topics:
  - natural_language_processing/topic_models
  - probabilistic_graphical_model
name: Multinomial Naive Bayes Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Multinomial Naive Bayes Model


>[!important] Definition
>Let $$x_{n} = (x_{n, 1} \,{,}\ldots{,}\, x_{n, L_{n}}) \in \{ 1 \,{,}\ldots{,}\, V\}^{L_{n}}$$ be **word representation** of **document** $n$ where
>- $x_{n, l}\in \{ 1 \,{,}\ldots{,}\,V \}$ is the $l$-th **word**,
>- $V$ is the **size** of **vocabulary**, 
>- $L_{n}$ is the **length** of document $n$.
> 
>Moreover, 
>- define $$m_{n} \in \{ 1 \,{,}\ldots{,}\, s \}$$ as a **latent variable** of document $n$
>	- $m_{n}$ represent the **topic allocation** for *the document*.    
>	- $m_{n}$ is from the *multinomial distribution* with parameter $\theta$
>	- $$\theta = (\theta_{1} \,{,}\ldots{,}\,\theta_{s}) \in \Delta_{s-1} := \left\{ (\theta_{1} \,{,}\ldots{,}\,\theta_{s}): \sum_{i=1}^{s}\theta_{i} = 1, \; \theta_{i} \in [0,1] \right\} $$
>- Let $$W = [w_{k,v}]\in [0,1]^{s \times V},$$ be the matrix whose **row** represents the **word distributions** for each **topic (row)** $$W_{k,:} = [w_{k,v}, v\in V] \in \Delta_{V-1}.$$
>  
>  
>The **Multinomial Naive Bayes Model** considers the following *latent variable model* for *each document* $n$:
>$$
>\left\{
>\begin{align*}
> \; p(m_{n}\,;\, \theta) &= \text{Multinomial}(m_{n}\;|\;\theta) \\[5pt]
> \; p(x_{n}\;|\; m_{n}, W) &=  \prod_{l=1}^{L_{n}}\text{Multinomial}(x_{n,l}\;|\; W_{m_{n}, :})
>\end{align*}
>\right.
>$$  
>where $w_{m_{n}}  := W_{m_{n}, :} \in \Delta_{V-1}$.

^b4ddab

- [[Naive Bayes Model]]
- [[Multinomial Distribution]]
- [[Latent Variable Models]]
- [[n-Gram Model and Language Model]]

![[naive_bayes_lda.png]]



## Explanation

>[!info]
>The *independence assumptions*
>- the *choice* of word at **different location** is independent given the same **topic**
>- the *word distribution* at **different location** is **identical** given the same **topic**. 
>	- in other word, the **parameter** for word distribution are **shared**

^3fc7af

>[!important]
>The **multinomial Naive Bayes** corresponds to the **bag-of-words representation** of documents. 

- [[Bag-of-Word Model for Document Representation]]

## Latent Dirichlet Allocation

>[!info]
>Compare *Multinomial naive Bayes* with *Latent Dirichlet Allocation*:
>- *Multinomial naive Bayes*
>	- assign one **topic** for each **document**
>	- the assignment follow multinomial distribution
>	- the **parameter** for multinomial distribution of assignment is **fixed** for *all documents*
>- *Latent Dirichlet Allocation*
>	- assign one **topic** for each **word**
>	- each document would have a **mixture of topics**
>	- the assignment follow multinomial distribution
>	- the **parameter** for multinomial distribution of assignment is **random** for *each documents*
>	- the parameter of assignment distribution follow a **Dirichlet prior distribution**

^1410e1


- [[Latent Dirichlet Allocation]]








-----------
##  Recommended Notes and References


- [[Naive Bayes Model]]
- [[Multinomial Distribution]]
- [[Multinomial Principle Component Analysis]]
- [[Factor Analysis]]
- [[Latent Variable Models]]


- [[Annealed Importance Sampling]]
- [[Gibbs Sampling]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Topic Models]]




- [[Probabilistic Graphical Models by Koller]] pp 769
- [[Speech and Language Processing by Jurafsky]] pp 57 - 62
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
