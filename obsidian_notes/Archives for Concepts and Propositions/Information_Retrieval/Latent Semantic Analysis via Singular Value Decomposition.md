---
tags:
  - concept
  - machine_learning/latent_variable_model
  - natural_language_processing/topic_models
  - information_retrieval/index
  - natural_language_processing/word_representation
  - LSA
  - latent_semantic_analysis
  - information_retrieval
keywords:
  - latent_semantic_analysis
topics:
  - information_retrieval/index
  - natural_language_processing/word_representation
  - natural_language_processing/topic_models
  - machine_learning_models
name: Latent Semantic Analysis via Singular Value Decomposition
date of note: 2024-11-05
---

## Concept Definition

>[!important]
>**Name**: Latent Semantic Analysis via Singular Value Decomposition

![[Co-Occurrence Matrix#^253cfb]]

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>A *term-document matrix* is a matrix $$X = [x_{i,d}] \in \mathbb{R}^{|\mathcal{V}| \times |\mathcal{D}|}$$ where
>- each entity counts the *occurrence* of given term $t_{i}$ in document $d$  $$x_{i,d} := x(t_{i}, d) = \sum_{j=1}^{n_{d}}\mathbb{1}\left\{ w_{j}^{d} = t_{i} \right\}$$
>  
>The **latent semantic analysis (LSA)** or **latent semantic index (LSI)**  finds the *low rank approximation* of the term-document matrix $X$.
>- Specifically,  the *singular value decomposition (SVD)* of $X$ $$X = U\Sigma\,V^{T}$$ where 
>	- $U\in \mathcal{O}(|\mathcal{V}|)$ contains the *eigenvectors* of $X X^{T}$ i.e. $$U\Lambda_{t}\,U^{T} = X X^{T}$$ 
>		- Note that  $X X^{T}$ contains all *inner product* between *word representation* $X_{i,:} \in \mathbb{R}^{|\mathcal{D}|}$
>	- $V\in \mathcal{O}(|\mathcal{D}|)$ contains the *eigenvectors* of $X^{T} X$ i.e. $$V\Lambda_{d}\,V^{T} = X^{T} X$$ 
>		- Note that  $X^{T} X$ contains all *inner product* between *document representation* $X_{:,d}$
>	- Assume that the *singular values* are sorted $$\sigma_{1} \,{\ge}\ldots{\ge}\,\sigma_{r}$$
>- The **LSA** find the **best rank-$k$ approximation** of $X$, i.e. $$\min_{\text{rank}(B) = k}\;\lVert X - B \rVert_{2}.$$ 
>	- The *Eckhart-Young Theorem* states that the best rank-$k$ approximation of $X$ as $$X_{k} := \sum_{i=1}^{k}\sigma_{i}\,u_{i}\,v_{i}^{T}:= U_{k}\,\Sigma_{k}\,V_{k}^{T}.$$ 
>	- Thus  $$\min_{\text{rank}(B) = k}\;\lVert X - B \rVert_{2} = \lVert X - X_{k} \rVert_{2} = \sigma_{k+1}.$$ 
>- We can now treat the term and document vectors as a **semantic space**.
>	- The **embedding** of a *document* $d_{j}\in \mathcal{D}$ is given by $$\hat{d}_{j} = \Sigma_{k}^{-1}\,U_{k}^{T}\,X_{:,j}  \in \mathbb{R}^{k}$$ as column of $X_{k}$
>		- The **LSA** maps the *document vector* from $|\mathcal{V}|$ to *$k$-dimensional*.
>		- For *query vector* $q\in \mathbb{R}^{|\mathcal{V}|}$, $$\hat{q} = \Sigma_{k}^{-1}\,U_{k}^{T}\,q$$
>		- The **cosine similarity** between documentds is given by $$\left\langle  \Sigma_{k}\hat{d}_{i} \,,\, \Sigma_{k}\hat{d}_{j}   \right\rangle$$
>		- The **cosine similarity** between documentds is given by $$\left\langle  \Sigma_{k}\hat{d}_{i} \,,\, \Sigma_{k}\hat{d}_{j}   \right\rangle$$
>	- The **embedding** of a *term* $t_{i}\in \mathcal{V}$ is given by $$\hat{t}_{i} = \Sigma_{k}^{-1}\,V_{k}^{T}\,X_{i,:}^{T}  \in \mathbb{R}^{k}$$ as row of $X_{k}$
>		- The **LSA** maps the *word vector* from $|\mathcal{D}|$ to *$k$-dimensional*.
>		- The **cosine similarity** between words is given by $$\left\langle  \Sigma_{k}\hat{t}_{i} \,,\, \Sigma_{k}\hat{t}_{j}   \right\rangle$$

- [[Co-Occurrence Matrix]]
- [[Singular Value Decomposition of Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Cosine Similarity and Cosine Distance]]
- [[Orthogonal Group]]
- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]
- [[Vector Space Model in Information Retrieval]]


## Explanation

### Dense Vector vs. Sparse Vector

![[Dense Text Retrieval with Pretrained Language Models#^2c7326]]

- [[Okapi BM25 score for Information Retrieval]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]
- [[Dense Text Retrieval with Pretrained Language Models]]

## Topic Models

- [[Topic Models]]

### Probabilistic Latent Semantic Analysis

- [[Probabilistic Latent Semantic Analysis or pLSA]]

### Latent Dirichlet Allocation

- [[Latent Dirichlet Allocation or LDA]]


-----------
##  Recommended Notes and References




- [[Principal Component Analysis or PCA]]




-----------
##  Recommended Notes and References




- [[Principal Component Analysis or PCA]]
- [[Information Retrieval]]


- [[Foundations of Statistical Natural Language Processing by Manning]] pp 554 - 566
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 954
- [[Speech and Language Processing by Jurafsky]] pp 130
- Wikipedia [Latent_semantic_analysis](https://en.wikipedia.org/wiki/Latent_semantic_analysis)