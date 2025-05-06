---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - natural_language_processing/topic_models
  - LDA
  - latent_dirichlet_allocation
keywords:
  - latent_dirichlet_allocation
  - LDA
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
>Finally, define $$m_{n,l} \in \{ 1 \,{,}\ldots{,}\, s \}$$ as a **latent variable** of word $x_{n,l}$.
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

- [[Multinomial Distribution]]
- [[Dirichlet Distribution]]
- [[Latent Variable Models]]
- [[Conjugate Prior Distribution for Bayesian Inference]]
- [[Multinomial Principle Component Analysis]]
- [[Alphabets and Strings Abstract Definition]]


![[latent_dirichlet_allocation.png]]

![[lda_jordan.png]]

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
>	- $W$ is *shared* for *multiple documents*
>	- each word $x_{n,l}$ is associated with a hidden variable $m_{n,l} \in \{ 1 \,{,}\ldots{,}\, s\}$
>	- hidden variable $m_{n,l}$ *assigns* each *word* to one of $s$ *topic*.
>	- the hidden variable $m_{n,l}$ follows the *multinomial distribution* whose parameters are from $z$
>	- the word $x_{n,l}$ follows the *multinomial distribution* whose parameters are from $W_{k,:}$ where $k=m_{n,l}$
>	- indexed by $l$

>[!info]
>*LDA* can be seen as a generalization of **multinomial PCA.**

- [[Multinomial Principle Component Analysis]]


## Multinomial Naive Bayes

>[!quote]
>In the **Bernoulli naive Bayes model**, we define a binary attribute (feature) $X_{i}$ to denote whether Bernoulli naive Bayes the $i$’th dictionary word $w_{i}$ *appears* in the document. This representation assumes that we care only about the *presence of a word*, not about how many times it appeared. Moreover, when applying the naive Bayes classifier with this representation we *assume* that the *appearance* of one word in the document is *independent* of the appearance of another (*given the document’s topic*). When learning a naive Bayes classifier with this representation, we learn frequency (over a document) of encountering each dictionary word in documents of specific categories — for example, the probability that the word “ball” appears in a document of category “sports.” We learn such a parameter for each pair (dictionary word, category). 
>
>In the **multinomial naive Bayes model**, we define attribute to describe the specific sequence of *multinomial naive Bayes words* in the document. The variable $X_{i}$ denotes *which dictionary word* appeared the $i$th word in the document. Thus, each $X_i$ can take on *many values*, one for each possible word. Here, when we use the naive Bayes classifier, we assume that the *choice* of word in *position* $i$ is *independent* of the choice of word in *position* $j$ (again, given the document’s topic). This model leads to a complication, since the distribution over $X_{i}$ is over all words in the document, which requires a large number of parameters. Thus, we further *assume* that the *probability* that a particular word is used in position $i$ does *not depend on* $i$; that is, the probability that $X_i = w$ (given the topic) is the same as the probability that $X_j = w$. In other words, we use *parameter sharing* between $P (X_{i} | C)$ and $P(X_{j}| C)$. This implies that the total number of parameters is again one for each (dictionary word, category).
>
>
>-- [[Probabilistic Graphical Models by Koller]] pp 767

![[Multinomial Naive Bayes Model#^1410e1]]

- [[Multinomial Naive Bayes Model]]
- [[Naive Bayes Model]]

![[naive_bayes_lda.png]]






-----------
##  Recommended Notes and References



- [[Multinomial Distribution]]
- [[Dirichlet Distribution]]

- [[Mean Field Approximation for PGM]]
- [[Variational Inference vs EM Algorithm]]
- [[Variational Inference for Clique Tree]]

- [[Probabilistic Latent Semantic Analysis or pLSA]]

- [[Annealed Importance Sampling]]
- [[Gibbs Sampling]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Topic Models]]

- [[Multinomial Principle Component Analysis]]
- [[Factor Analysis]]
- [[Latent Variable Models]]


- [[Probabilistic Graphical Models by Koller]] pp 769
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 47 - 49
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 953 - 957
- [[Elements of Statistical Learning by Hastie]]