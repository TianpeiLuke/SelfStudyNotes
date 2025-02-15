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
name: Information Retrieval
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Information Retrieval

>[!important] Definition
>**Information retrieval** is the task of finding documents $d\in \mathcal{D}$ that are *relevant* to a user’s need (*query*) $q$ for   information.

>[!important] Definition
>**Information retrieval (IR)** is finding material (usually documents) of an *unstructured nature* (usually text) that *satisfies* an *information need* from within large collections (usually stored on computers).
>
>--  [[Introduction to Information Retrieval by Manning]] pp 1

>[!important] Definition
>The **information retrieval (IR)** is the name of the field encompassing the *retrieval* of all  manner of media based on *user information needs*.
>- A *information retrieval system* is called a **search engine**.
>  
>  
>An **ad hoc retrieval** task is completed by following steps:
>- user poses a *query* to the information retrieval system
>- the system returns a *ordered set* of *documents* from some *collection.*
>  
>where    
>- a **term** refers to words or phrases in a collection.
>- A **query** represents the *user information need* in a few terms.
>- A **document** refers to a basic unit of text the system *indexes* and *retrieves*
>- A **collection** refers to a set of *documents* being used to satisfy user requests.


![[information_retrieval_system.png]]


![[information_text_retrieval.png]]

### Indexing

>[!important] Definition
>**Indexing** is the process to provide **index** for documents before *query* so that the system can avoid *linearly scanning*  the texts for each query. 

- [[Co-Occurrence Matrix]]
- [[Inverted Index for Information Retrieval]]


### Similarity Search

- [[Similarity Search]]
- [[Approximate Nearest Neighbor Search]]


### Metrics

- [[Recall and Precision and F-Measure]]
- [[Precision-Recall Curve]]
- [[Recall and Precision at k]]
- [[Interpolated Precision and Interpolated Average Precision]]
- [[Mean Average Precision and Average Precision]]
- [[Normalized Discounted Cumulative Gain or NDCG]]
- [[Mean Reciprocal Rank or MRR for Ranking and Question Answering]]



### Information Extraction

- [[Information Extraction]]

### Sparse Retrieval

- [[Vector Space Model in Information Retrieval]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]
- [[Okapi BM25 score for Information Retrieval]]

### Dense Retrieval

- [[Distributed Representation]]
- [[Dense Text Retrieval with Pretrained Language Models]]
- [[ColBERT as Multi-Representation Bi-Encoder Structure for Dense Information Retrieval]]



## Explanation

>[!info]
>The purpose of **storing an index** is to *optimize speed* and *performance* in finding relevant documents for a search query.



## LLM for Information Retrieval

- Zhu, Y., Yuan, H., Wang, S., Liu, J., Liu, W., Deng, C., ... & Wen, J. R. (2023). Large language models for information retrieval: A survey. _arXiv preprint arXiv:2308.07107_.
- Zhao, W. X., Liu, J., Ren, R., & Wen, J. R. (2024). Dense text retrieval based on pretrained language models: A survey. _ACM Transactions on Information Systems_, _42_(4), 1-60. 


## Question Answering

- [[Question Answering Problem]]



-----------
##  Recommended Notes and References

- [[Vector Space Model in Information Retrieval]]
- [[Matrix]]
- [[Topic Models]]
- [[Bag-of-Word Model for Document Representation]]



- [[Introduction to Information Retrieval by Manning]] pp 1
- [[Speech and Language Processing by Jurafsky]] pp 108
- [[Handbook of Natural Language Processing by Indurkhya]] pp 455 - 485
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 529
- [[Artificial Intelligence Modern Approach by Russell]] pp 867

- Zhao, W. X., Liu, J., Ren, R., & Wen, J. R. (2024). Dense text retrieval based on pretrained language models: A survey. _ACM Transactions on Information Systems_, _42_(4), 1-60. 

- Youtube
	- [Applied Machine Learning for Ranking Products in an Ecommerce Setting Arnoud de Munnik Wehkamp Jerry](https://www.youtube.com/watch?v=6BGCn3h59nA)