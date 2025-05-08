---
tags:
  - concept
  - information_retrieval/query_expansion
  - QE
  - query_expansion
  - information_retrieval
keywords:
  - query_expansion
topics:
  - information_retrieval/query_expansion
name: Query Expansion for Information Retrieval
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Query Expansion for Information Retrieval

>[!important] Definition
>**Query expansion** is a set of techniques for *reformulating a user’s original query into a richer, often longer, query* so that the retrieval system can match more relevant documents that would otherwise be missed. 
>- The *goal* is to reduce vocabulary mismatch and *improve recall* without sacrificing precision.

- [[Information Retrieval]]
- [[Relevance Feedback for Information Retrieval]]

## Explanation

### Benefits & trade-offs

> [!important]
>- **+** Higher recall, especially for short queries and synonym-rich domains.
>     
> - **+** Robust to spelling variants and abbreviations.
>     
> - **–** Risk of **query drift**: added terms may steer results off-topic → lower precision.
>     
> - **–** Additional computation (feedback round-trip, embedding search).
>     


>[!info]
> Mitigation techniques include 
> - *term-selection thresholds*, 
> - *contextual similarity*, 
> - and *user-controlled expansion suggestions* (“Did you mean…?”).


## Query Expansion Workflow

>[!important]
>The typical **query expansion** works as follows
>- **Start with the user query** 
>	- _Example:_ `heart attack symptoms`
>- **Generate expansion terms** from one or more sources:
>     
>    - **Global statistics**
> 	   - *term co-occurrence*, [[Co-Occurrence Matrix]]
> 	   - *word embeddings*, [[Word Embedding]]
> 	   - thesauri (e.g., WordNet).
>         
>    - **Collection feedback**
> 	   - *pseudo-relevance feedback* (PRF): [[Relevance Feedback for Information Retrieval]]; [[Pseudo-Relevance Feedback or PRF]]
> 		   - assume top-$k$ results are relevant, 
> 		   - harvest frequent terms.
>         
>    - **Knowledge bases**
> 	   - *entity synonyms*, 
> 	   - *ontologies* (e.g., UMLS, Wikipedia redirects).
>         
>    - **User context**
> 	   - *past queries*, 
> 	   - *session history*, 
> 	   - *location*.
>         
>- **Weight or filter** 
>	- the candidate terms using 
> 		- *tf-idf*, [[Term Frequency and Inverse Document Frequency or TF-IDF]]
> 		- *KL-divergence*, [[Kullback-Leibler Divergence]]
> 		- *cosine similarity* in embedding space, [[Cosine Similarity and Cosine Distance]]
> 		- or *learning-to-rank* heuristics. [[Ranking as Learning Problem]]
>     
> - **Construct the expanded query** by appending or interpolating the *new terms*, often with lower weights than the originals:   $$Q_{\text{final}} \;=\; \alpha\,Q_{\text{orig}} \;+\; (1-\alpha)\,Q_{\text{exp}}$$​
> 	- where $\alpha\in[0,1]$ controls how strongly the system trusts the original wording.
>     
> - **Run retrieval** with the expanded query and rank documents.
> 



## Query Expansion Methos

### Classic methods

| Method                     | Key idea                                                                                                      |
| -------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Rocchio (PRF)**          | Adjusts the original query vector toward the *centroid of top-k retrieved docs*, away from non-relevant ones. |
| **Relevance Models (RM3)** | Estimates a *relevance language model* from pseudo-relevant docs and interpolates with the *query model*.     |
| **Embedding QE**           | Adds *nearest-neighbor words* in word2vec/BERT space (e.g., “myocardial”, “infarction” for “heart attack”).   |
| **Concept-based QE**       | Expands with synonyms and related concepts from medical/legal *taxonomies*.                                   |





-----------
##  Recommended Notes and References


- [[Introduction to Information Retrieval by Manning]] pp 189 - 193