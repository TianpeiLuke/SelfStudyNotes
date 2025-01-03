---
tags:
  - concept
  - natural_language_processing
  - information_retrieval
keywords:
  - information_retrieval
  - colbert_method
topics:
  - information_retrieval
  - natural_language_processing
name: ColBERT for Information Retrieval
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: ColBERT for Information Retrieval

![[Dense Text Retrieval with Pretrained Language Models#^d1dcfd]]

![[Dense Text Retrieval with Pretrained Language Models#^551842]]

>[!important] Definition
>The **ColBERT** consists of three parts
>- **Query encoder**: 
>	- Given a query, it first apply the *WordPiece tokenization* and convert it into tokens $$q = q^{0}q^{1}\,{}\ldots{}\,q^{l}$$ 
>	- and we append these tokens *after* `[CLS]` token. 
>	- If the sequence is less than the pre-defined window size, we would *pad* it with `[MASK]` token.
>	- This process of the *padding* with *masked tokens* is denoted as **query augmentation**.
>	- The output representation of each token then passes through a *linear layer without activations*.
>- **Document encoder**: The document encoding is similar to query encoding
>	- We first tokenize the documents into $$d= d^{0}d^{1}\,{}\ldots{}\,d^{n}$$
>	- We then prepend the token `[CLS]` in the front of sentence.
>	- Unlike query embedding, document embedding do not use *query augmentation.*
>	- After the linear layer, the document encoder has an additional **filter**, which *filters out* the embedding corresponding to the *punctuation symbols*.
>	- This filter reduce the number of embeddings.
>- **Late Interaction**:
>	- The *late interaction* computes the *relevance score* between encoded query tokens and document tokens via the *sum* of *maximum similarity* between *each query vector* and *all document vectors*.
>
>
>Specifically, given the *query* $$q = q^{0}q^{1}\,{}\ldots{}\,q^{l}$$ and *document* $$d = d^{0}d^{1}\,{}\ldots{}\,d^{n},$$ the **ColBERT** computes the *bags of embeddings* in the following ways:
>- The *query embedding* is given by $$E_{q} = \text{Normalize}\left(\text{CNN}\left(\text{BERT}(s)\right)\right)$$ where the query prompt is given by the **query augmentation** $$s = \text{[Q]}\;q^0q^{1}\ldots q^{l}\;\text{[MASK]}\,{}\ldots{}\,\;\text{[MASK]}$$
>- The *document embedding* is given by $$E_{d} = \text{Filter}\left(\text{Normalize}\left(\text{CNN}\left(\text{BERT}(s')\right)\right)\right)$$ where the document prompt is given by $$s' = \text{[D]}\;d^0d^{1}\ldots d^{n}$$
>- The *late interaction* estimates the *relevance score* between the *bags of contextualized embeddings* of query $q$ and document $d$ via $$S(q, d) := \sum_{i\in E_{q}}\,\max_{j\in E_{d}} \left\langle  E_{q_{i}}\,,\, E_{d_{j}}   \right\rangle$$

- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[WordPiece Tokenization]]
- [[Word Basic Concepts]]
- [[Bag-of-Word Model for Document Representation]]
- [[Cosine Similarity and Cosine Distance]]


![[colbert_inference.png]]

![[colbert_architecture.png]]



## Explanation

>[!quote]
>**Query augmentation** is used as a *soft, differentiable* mechanism for learning to *expand queries* with new terms, or to *reweigh existing terms* based on their importance for matching the query
>
>-- [[khattabColBERTEfficientEffective2020]] pp 42


![[information_dense_retrieval_one_two_encoder.png]]


- [[Contrastive Learning]]
- [[Representation Learning]]
- [[Retrieval Augmented Generation]]




-----------
##  Recommended Notes and References


- [[Dense Text Retrieval with Pretrained Language Models]]
- [[Information Retrieval]]
- [[Masked Language Modeling as Language Model Training Task]]
- [[Large Language Model and Pretrained Language Models]]

- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp 298 - 301
- [[khattabColBERTEfficientEffective2020]] Khattab, O., & Zaharia, M. (2020, July). Colbert: Efficient and effective passage search via contextualized late interaction over BERT. In _Proceedings of the 43rd International ACM SIGIR conference on research and development in Information Retrieval_ (pp. 39-48).
