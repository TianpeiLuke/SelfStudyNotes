---
tags:
  - concept
  - natural_language_processing
  - information_retrieval
keywords:
  - information_retrieval
topics:
  - information_retrieval
  - natural_language_processing
name: Information Retrieval with Encoder Language Models
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Information Retrieval with Encoder Language Models

### Information Retrieval with Dense Vectors



- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Information Retrieval]]

### Cross-Encoder Structure

>[!important] Definition
>The **cross-encoder** considers a *query-document pair* as an entire "sentence".
>
>In specific, the **cross-encoder approach** for *dense retrieval* is described as following steps
>- *Encode* the query and document via a *single encoder*
>	- The input of encoder is the *concatenation* of a query $q$ and a document $d$, separated by *special token* `[SEP]` $$x = q + \text{`[SEP]'} + d$$
>	- Compute the *embedding* for the special token `[CLS]` in the beginning of sentence $$z = \text{BERT}(x)[\text{CLS}]$$
>- The *relevance score* is computed via a *linear layer* on the top of embedding as $$\text{relevancy-score}(q, d) := \text{softmax}(Uz)$$

^d1dcfd

- [[Softmax Function and Log-Sum-Exp Function]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]

### Bi-Encoder Structure

>[!important] Definition
>The **bi-encoder** or **dual-encoder** adopts the *two-tower architecture*:
>- It has *two encoders*: **query encoder** and **document encoder**. $$\text{BERT}_{\mathcal{Q}}, \quad \text{BERT}_{\mathcal{D}}$$
>- This is similar to the *representation learning approach* 
>
>
>In specific, the **bi-encoder approach** for *dense retrieval* is described as following steps
>- Encode each document $d$ via *document encoder* $$z_{d} = \text{BERT}_{\mathcal{D}}(d)[\text{CLS}]$$
>- Store all document embeddings in a vector database
>- *Encode* the query  $q$ via *query encoder* $$z_{q} = \text{BERT}_{\mathcal{Q}}(q)[\text{CLS}]$$
>- The *relevance score* is computed via a *cosine similarity* between query and document embedding $$\text{relevancy-score}(q, d) := \left\langle  z_{q}\,,\, z_{d}   \right\rangle$$

^551842

- [[Siamese Network for Contrastive Learning]]
- [[Cosine Similarity and Cosine Distance]]
- [[Contrastive Learning]]
- [[Representation Learning]]

![[information_dense_retrieval_one_two_encoder.png]]

### ColBERT as Multi-Representation Bi-encoder

- [[ColBERT as Multi-Representation Bi-Encoder Structure for Dense Information Retrieval]]




## Explanation

>[!quote]
>The **classic tf-idf** or **BM25 algorithms** for IR have long been known to have a conceptual flaw:
> - they work only if there is *exact overlap* of words between the *query*  and *document*. 
> - In other words, the user posing a query (or asking a question) needs  to guess exactly what words the writer of the answer might have used, an issue called  the **vocabulary mismatch problem**.
>- The solution to this problem is to use an approach that can handle **synonymy**:  
>	- instead of (sparse) word-count vectors, using **(dense) embeddings**. 
>	- This idea was  first proposed for retrieval in the last century under the name of **Latent Semantic  Indexing** approach (Deerwester et al., 1990), but is implemented in modern times  via encoders like **BERT**.  
>
>-- [[Speech and Language Processing by Jurafsky]] pp 298

^2c7326

- [[Latent Semantic Analysis via Singular Value Decomposition]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]
- [[Okapi BM25 score for Information Retrieval]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


- [[Retrieval Augmented Generation]]




-----------
##  Recommended Notes and References


- [[Large Language Model and Pretrained Language Models]]

- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp 298 - 301
- Zhao, W. X., Liu, J., Ren, R., & Wen, J. R. (2024). Dense text retrieval based on pretrained language models: A survey. _ACM Transactions on Information Systems_, _42_(4), 1-60. [[zhaoDenseTextRetrieval2024]]
