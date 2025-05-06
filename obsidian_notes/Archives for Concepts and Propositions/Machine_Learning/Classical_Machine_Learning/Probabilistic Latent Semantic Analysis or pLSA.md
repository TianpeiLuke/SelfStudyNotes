---
tags:
  - concept
  - natural_language_processing/topic_models
  - machine_learning/models
  - probabilistic_graphical_models/models
  - information_retrieval/index
  - information_retrieval/model
  - PLSA
  - probabilistic_latent_semantic_analysis
  - information_retrieval
  - information_retrieval/ranking
keywords:
  - PLSA
  - probabilistic_latent_semantic_analysis
topics:
  - information_retrieval
name: Probabilistic Latent Semantic Analysis
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Probabilistic Latent Semantic Analysis

![[Co-Occurrence Matrix#^253cfb]]


>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>A *term-document matrix* is a matrix $$X = [x_{i,d}] \in \mathbb{N}_{\ge 0}^{|\mathcal{V}| \times |\mathcal{D}|}$$ where $x_{i,d}$ represents the frequency of term $t_i$ in document $d$.
>
>**Probabilistic Latent Semantic Analysis (PLSA)** is a statistical model that aims to find *latent topics* that explain the co-occurrence of words in documents.
>- Denote a latent variable $z \in \mathcal{Z} = \{z_1, \ldots, z_k\}$, where $k$ is the number of topics. 
>  
>  
>PLSA models the *probability* of observing a word $w$ in a document $d$ as a mixture of conditionally independent multinomial distributions over topics:
>$$P(w, d) = P(d) P(w | d) = P(d) \sum_{z \in \mathcal{Z}} P(w | z) P(z | d)$$
>where:
>- $P(d)$ is the probability of observing *document* $d$.
>- $P(z | d)$ is the probability of *topic* $z$ given document $d$. 
>	- This can be seen as the *document*'s *topic distribution.*
>- $P(w | z)$ is the probability of *word* $w$ given topic $z$. 
>	- This can be seen as the *topic*'s *word distribution*.

^bcf83a

- [[Co-Occurrence Matrix]]
- [[Factor Analysis]]
- [[Latent Variable Models]]



### Observed Likelihood Function

>[!important] Definition
>The goal of **PLSA** is to estimate the parameters $P(z | d)$ and $P(w | z)$ that maximize the *likelihood* of the *observed term-document matrix* $X$. 
>
>The likelihood function is given by:
>$$\mathcal{L} = \prod_{d \in \mathcal{D}} \prod_{w \in \mathcal{V}} P(w, d)^{n(w, d)} = \prod_{d \in \mathcal{D}} \prod_{i=1}^{|\mathcal{V}|} \left( P(d) \sum_{j=1}^{k} P(t_i | z_j) P(z_j | d) \right)^{x_{i,d}}$$
>where $n(w, d)$ (or $x_{i,d}$) is the observed count of word $w$ (or term $t_i$) in document $d$.

- [[Evidence Lower Bound]]
- [[Marginalized Likelihood Function]]

### EM Algorithm

>[!important] Definition
>The parameters are typically estimated using the **Expectation-Maximization (EM) algorithm**:
>
>- *Require*: Term-document matrix $X$
>- *Require*: Number of latent topics $k$
>- *Initialize*: Randomly initialize 
>	- $P(z | d)$ for all $d \in \mathcal{D}, z \in \mathcal{Z}$ 
>	- $P(w | z)$ for all $w \in \mathcal{V}, z \in \mathcal{Z}$ such that they are non-negative and sum to 1 over the appropriate variables.
>- **Iterate until convergence:**
>	- **Expectation (E) step:** For each document $d$, word $w$, and topic $z$, compute the *posterior probability* of the *topic* given the *document* and the *word*:
>		$$P(z | w, d) = \frac{P(w | z) P(z | d)}{\sum_{z' \in \mathcal{Z}} P(w | z') P(z' | d)}$$
>	- **Maximization (M) step:** Update the model parameters based on the posterior probabilities calculated in the E step:
>		- $$P(w | z) = \frac{\sum_{d \in \mathcal{D}} n(w, d) P(z | w, d)}{\sum_{w' \in \mathcal{V}} \sum_{d \in \mathcal{D}} n(w', d) P(z | w', d)}$$
>		- $$P(z | d) = \frac{\sum_{w \in \mathcal{V}} n(w, d) P(z | w, d)}{\sum_{z' \in \mathcal{Z}} \sum_{w \in \mathcal{V}} n(w, d) P(z' | w, d)} = \frac{\sum_{i=1}^{|\mathcal{V}|} x_{i,d} P(z | t_i, d)}{\sum_{j=1}^{k} \sum_{i=1}^{|\mathcal{V}|} x_{i,d} P(z_j | t_i, d)}$$
>- *Return*: Estimated topic-word distributions $P(w | z)$ and document-topic distributions $P(z | d)$.

- [[Expectation-Maximization Algorithm]]
- [[Expectation-Maximization Algorithm for Exponential Family]]
- [[Multinomial Distribution]]




## Explanation

### Document Embedding and Topic Embedding

>[!important] Definition
>**Interpretation:**
>- $P(z | d)$ represents the **topic mixture of document** $d$. 
>	- A document can be represented as a *probability distribution* over the latent topics.
>	- $P(z |d)$ can be seen as a **document embedding**.
>- $P(w | z)$ represents the **word distribution of topic** $z$. 
>	- Each topic is characterized by a probability distribution over the vocabulary.
>	- $P(w | z)$ can be seen as a **topic embedding**.

- [[Word Embedding]]



>[!info]
>PLSA provides a probabilistic framework for **topic modeling**, offering a more principled approach compared to the *linear algebra-based LSA*. 
>
>However, the number of parameters in PLSA grows linearly with the *number of documents*, which can lead to *overfitting*, especially for large document collections.

- [[Topic Models]]


### Compare PLSA, Multinomial PCA and Multinomial Naive Bayes

>[!info]
>- Both **pLSA** and **Multinomial PCA** factorise the term–document count matrix into two low‑rank non‑negative factors but differ in interpretation: 
>	- **pLSA** constrains columns of $\phi$ and $\theta$ to be _probability simplices_ (topics), 
>	- while **multinomial/Poisson‑PCA** allows *unconstrained* non‑negative loadings resembling an **NMF**.
 >   
>- **Naïve Bayes** also fits word multinomials, yet ties them _to labels_ instead of latent variables, so it is supervised and yields no low‑rank representation.




## Related Work

### Latent Semantic Analysis

- [[Co-Occurrence Matrix]]
- [[Latent Semantic Analysis via Singular Value Decomposition]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]

### Latent Dirichlet Allocation

- [[Latent Dirichlet Allocation]]
- [[Probabilistic Graphical Models]]



-----------
##  Recommended Notes and References






- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 954
- Wikipedia [Probabilistic_latent_semantic_analysis](https://en.wikipedia.org/wiki/Probabilistic_latent_semantic_analysis)