---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - natural_language_processing/topic_models
keywords:
  - latent_dirichlet_allocation
topics:
  - natural_language_processing/topic_models
  - probabilistic_graphical_model
name: Latent Dirichlet Allocation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Latent Dirichlet Allocation


>[!important] Definition
>Let $$x_{n} = (x_{n, 1} \,{,}\ldots{,}\, x_{n, L_{n}}) \in \{ 1 \,{,}\ldots{,}\, V\}^{L_{n}}$$ be **word representation** of **document** $n$ where
>- $x_{n, l}\in \{ 1 \,{,}\ldots{,}\,V \}$ is the $l$-th **word**,
>- $V$ is the **size** of **vocabulary**, 
>- $L_{n}$ is the **length** of document $n$.
>  
>The probability of observing word $v$ at location $l$ of document $n$ is given by a *multinomial distribution* where
>$$
>\mathcal{P}\left(x_{n,l} = v \;|\; z_{n}\right) = \sum_{k=1}^{s}\,z_{n,k}\,w_{k, v}
>$$
>where 
>- each $z_{n,k} \in [0,1]$ defines the **proportion** of **topic** $k$ in document $n$. $$z_{n} =  (z_{n, 1} \,{,}\ldots{,}\,z_{n, s}) \in \Delta_{s-1}.$$
>- Assume that there are in **total $s$ topics** in the document.
>- $z_{n}$ has **Dirichlet prior** $$z_{n} \sim \text{Dirichlet}(z_{n}|\alpha)$$
>- $$W = [w_{k,v}]\in [0,1]^{s \times V},$$ is the matrix whose **row** represents the **word distributions** for each **topic (row)** $$W_{k,:} = [w_{k,v}, v\in V] \in \Delta_{V-1}.$$
>- Denote $p_{n,v} := \mathcal{P}\left(x_{n,l} = v \;|\; z_{n}\right)$, then  $$p_{n} = (p_{n,1} \,{,}\ldots{,}\,p_{n,V}) = z_{n}^{T}\,W \in \Delta_{v-1}$$
>- $$\sum_{v\in V}\mathcal{P}\left(x_{n,l} = v \;|\; z_{n}\right) = 1 \implies z_{n}^{T}\,W\,1_{V} = 1$$
>  
>Finally, define $$m_{n,l} \in \{ 1 \,{,}\ldots{,}\, s \}$$ be a **latent variable** of word $x_{n,l}$.
>- $m_{n,l}$ represent the **topic allocation**.    
>- Denote $m_{n} := (m_{n, 1} \,{,}\ldots{,}\,m_{n, L_{n}})$  
>  
>The **latent Dirichlet allocation (LDA)** considers the following *latent variable model* for *each document* $n$:
>$$
>\left\{
>\begin{align*}
> p(z_{n}) &= \text{Dirichlet}(z_{n}\;|\; \alpha) \\[5pt]
> p(W) &= \prod_{k=1}^{s}\text{Dirichlet}(W_{k,:}\;|\; \beta) \\[5pt]
> \; p(m_{n}\;|\; z_{n}) &= \prod_{l=1}^{L_{n}}\text{Multinomial}(m_{n,l}\;|\;z_{n}) \\[5pt]
> \; p(x_{n}\;|\; m_{n}, W) &=  \prod_{l=1}^{L_{n}}\text{Multinomial}(x_{n,l}\;|\; W_{m_{n, l}, :})
>\end{align*}
>\right.
>$$  
>where $w_{m_{n, l}}  := W_{m_{n, l}, :} \in \Delta_{V-1}$

- [[Multinomial Random Variable]]
- [[Dirichlet Random Variable]]
- [[Latent Variable Models]]


![[latent_dirichlet_allocation.png]]

## Explanation

>[!info]
>Three layers of representation in LDA
>- **multiple documents** for each corpus: 
>	- assume all documents are independent
>	- indexed by $n$
>- **multiple topics** for each document:
>	- total $s$ distinct topics
>	- the *distribution of topic* for given document $n$ is represented by vector $z_{n} \in \Delta_{s-1}$
>	- prior of $z$ is *Dirichlet*
>	- indexed by $k$
>- **multiple words** for each topic:
>	- total $V$ distinct words (*vocabulary*)
>	- a word in $l$ position is denoted as $x_{n,l}$
>	- the *distribution of words* for each topic $k$ is represented by *row of* $W$, $W_{k,:} \in \Delta_{V-1}$
>	- prior of $W_{k,:}$ is *Dirichlet*.
>	- each word $x_{n,l}$ is associated with a hidden variable $m_{n,l} \in \{ 1 \,{,}\ldots{,}\, s\}$
>	- hidden variable $m_{n,l}$ *assigns* each *word* to one of $s$ *topic*.
>	- the hidden variable $m_{n,l}$ follows the *multinomial distribution* whose parameters are from $z$
>	- the word $x_{n,l}$ follows the *multinomial distribution* whose parameters are from $W_{k,:}$ where $k=m_{n,l}$
>	- indexed by $l$

>[!info]
>*LDA* can be seen as a generalization of **multinomial PCA.**

- [[Multinomial Principle Component Analysis]]




-----------
##  Recommended Notes and References



- [[Multinomial Random Variable]]
- [[Dirichlet Random Variable]]

- [[Mean Field Approximation]]
- [[Variational Inference vs EM Algorithm]]
- [[Variational Inference for Clique Tree]]

- [[Probabilistic Latent Semantic Analysis]]

- [[Annealed Importance Sampling]]
- [[Gibbs Sampling]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Topic Models]]

- [[Multinomial Principle Component Analysis]]
- [[Factor Analysis]]
- [[Latent Variable Models]]


- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 953 - 957
- [[Elements of Statistical Learning by Hastie]]