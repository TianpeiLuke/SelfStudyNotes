---
tags:
  - concept
  - natural_language_processing
  - natural_language_processing/word_representation
  - information_retrieval/term_representation
keywords:
  - co-occurrence_matrix
  - term_document_matrix
topics:
  - natural_language_processing/word_representation
name: Co-Occurrence Matrix
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Co-Occurrence Matrix

### Term-Document Matrix

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>A **term-document matrix** is a matrix $$X = [x_{i,d}] \in \mathbb{R}^{|\mathcal{V}| \times |\mathcal{D}|}$$ where
>- each *row* represents a **word** or **token** $t_{i}\in \mathcal{V}$
>- and each *column* represents a **document** $d\in \mathcal{D}$
>- Each entity counts the *occurrence* of given word $w_{i}$ in document $d$  $$x_{i,d} := x(t_{i}, d) = \sum_{j=1}^{n_{d}}\mathbb{1}\left\{ w_{j}^{d} = t_{i} \right\}$$
>- We can covert the count into **frequency** by *normalizing it for each document (column)* $$\hat{p}_{i,d} = \frac{x_{i,d}}{\sum_{w_{i}\in d}x_{i,d}}$$

^253cfb

- [[Matrix]]
- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]

### Term-Term Matrix or Term-Context Matrix

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be a *corpus* i.e. the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>A **term-term matrix** or **word-word matrix** or **term-context matrix** is a matrix $$C = [c_{i,j}] \in \mathbb{R}^{|\mathcal{V}| \times |\mathcal{V}|}$$ where
>- the *row* represents a **target word** $t_{i}\in \mathcal{V}$
>- and the *column* represents a **context word** $w_{j}\in \mathcal{V}$
>- Each entry represents the **number of co-occurrence** the *target word (row)* and *context word (column)* within some *context* in the corpus $\mathcal{D}$.
>- The **context** could be 
>	- the entire document $d$, then the *term-context matrix* becomes $$c_{i,j} := \sum_{d\in \mathcal{D}}\mathbb{1}\left\{ t_{i}\in d\, \land \, t_{j} \in d \right\}$$
>	- or within a *context window* $$b_{i}^{d} := B(w_{i}^{d}, r) := \left\{ w_{i-r}^{d}\,{,}\ldots{,}\,w_{i}^{d} \,{,}\ldots{,}\,w_{i+r}^{d} \right\},$$ then  *term-context matrix* becomes $$c_{i,j} := \sum_{d\in \mathcal{D}}\sum_{i=1}^{n_{d}}\mathbb{1}\left\{ t_{j} \in  b_{i}^{d} \right\}$$


## Explanation

>[!info]
>The **term-document matrix** is introduced in the **vector space model** where each column represents the document $d$ in a *vector space of documents*.

- [[Vector Space Model in Information Retrieval]]




-----------
##  Recommended Notes and References

- [[Vector Space Model in Information Retrieval]]

- [[Topic Models]]


- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp 106 - 110
- [[Probabilistic Graphical Models by Koller]]