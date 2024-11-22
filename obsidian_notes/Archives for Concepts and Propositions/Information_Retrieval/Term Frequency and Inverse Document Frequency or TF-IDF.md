---
tags:
  - concept
  - natural_language_processing
  - information_retrieval/relevancy_metric
  - information_retrieval/index
keywords:
  - tf_idf_representation
topics:
  - information_retrieval/index
  - natural_language_processing/word_representation
name: Term Frequency and Inverse Document Frequency or TF-IDF
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Term Frequency and Inverse Document Frequency or TF-IDF

![[Co-Occurrence Matrix#^253cfb]]

- [[Co-Occurrence Matrix]]

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>Denote the *term-document matrix* as $$X = [x_{i,d}] \in \mathbb{R}^{|\mathcal{V}| \times |\mathcal{D}|}$$ where each entity counts the *occurrence* of given token $t_{i}$ in document $d$  $$x_{i,d} = \sum_{j=1}^{n_{d}}\mathbb{1}\left\{ w_{j}^{d} = t_{i} \right\}$$
>
>The **term frequency** of a *term* $t_{i}\in \mathcal{V}$ in *document* $d\in \mathcal{D}$ is given by 
>$$
>\text{tf}_{i,d} := \text{tf}(t_{i}, d) = \left\{\begin{array}{cl}1 + \log_{10}(x_{i,d}) & \text{if }x_{i,d} >0 \\[8pt] 0 &\text{otherwise} \end{array}\right. 
>$$

>[!important] Definition
>The **document frequency** of a term $t_{i}\in \mathcal{V}$ is given by the *number of documents* it occurs in.
>$$
>\text{df}_{i} := \text{df}(t_{i}) = \sum_{d\in \mathcal{D}}x_{i,d}
>$$

>[!important] Definition
>The **inverse document frequency** or **idf term weight** of a term $t_{i}\in \mathcal{V}$ is given by 
>$$
>\text{idf}_{i} := \text{idf}(t_{i}) = \log_{10}\left( \frac{|\mathcal{D}|}{\text{df}_{i}} \right)  = \log_{10}\left( \frac{|\mathcal{D}|}{\sum_{d\in \mathcal{D}}x_{i,d}} \right) 
>$$
>The **idf term weight** emphasizes the *discriminative words.*
>- The fewer documents in which a term occurs, the higher this weight.

>[!important] Definition
>The  **tf-idf weighted value** of a term $t_{i}\in \mathcal{V}$ in a document $d\in \mathcal{D}$ is given by 
>$$
>\begin{align*}
>&\text{tf-idf}_{i,d} \\[8pt]
>&:= \text{tf-idf}(t_{i},d) := \text{tf-idf}(X_{i,:}) \\[8pt]
>&= \text{tf}_{i,d} \times \text{idf}_{i} \\[8pt]
>&= \left\{\begin{array}{cl} \left( 1 + \log_{10}(x_{i,d})  \right)\;\log_{10}\left( \dfrac{|\mathcal{D}|}{\sum_{d\in \mathcal{D}}x_{i,d}} \right) & \text{if }x_{i,d} >0 \\[8pt] 0 &\text{otherwise} \end{array}\right.
>\end{align*}
>$$

>[!info]
>A naive definition of **tf-idf term weight** is given by 
>$$
>\begin{align*}
>&\text{tf-idf}_{i,d} \\[8pt]
>&:= \text{tf-idf}(t_{i},d) := \text{tf-idf}(X_{i,:}) \\[8pt]
>&= \left\{\begin{array}{cl} x_{i,d}\;\log_{10}\left( \dfrac{|\mathcal{D}|}{\sum_{d\in \mathcal{D}}x_{i,d}} \right) & \text{if }x_{i,d} >0 \\[8pt] 0 &\text{otherwise} \end{array}\right.
>\end{align*}
>$$

### Query Score

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>- Let $Q\in \mathcal{V}^{*}$ be a *query document* with $k$ *keywords* $q_{1}\,{,}\ldots{,}\,q_{k}$.
>  
>Then the **tf-idf score** of *document* $d$ is given by the sum of all *tf-idf weights*  of each term $q$ in $d$ 
>$$
>\text{tf-idf score}(Q, d) = \sum_{j=1}^{k}\text{tf-idf}(q_{j}, d)
>$$
>- This is a **overlap score measure.**



## Explanation

>[!quote]
>The **tf-idf weighting** is the way for *weighting co-occurrence matrices* in *information retrieval*, but also plays a role in many other aspects of natural language processing.
>- It’s also a great baseline, the simple thing to try first.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 113  

>[!info]
>An alternative formulation of **IDF** or **inverse document frequency** is given by 
>$$
>\text{idf}_{i} := \log_{10}\left( \frac{|\mathcal{D}| - \text{df}_{i} + \frac{1}{2} }{\text{df}_{i} + \frac{1}{2}} \right)
>$$


-----------
##  Recommended Notes and References



- [[Vector Space Model in Information Retrieval]]
- [[Matrix]]
- [[Topic Models]]


- [[Introduction to Information Retrieval by Manning]] pp 117 - 119
- [[Speech and Language Processing by Jurafsky]] pp 111 - 114