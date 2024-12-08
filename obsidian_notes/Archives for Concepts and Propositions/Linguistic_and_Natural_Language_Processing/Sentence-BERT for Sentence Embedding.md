---
tags:
  - concept
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - natural_language_processing/sentence_representation
  - information_retrieval/retrieval_augmentation
keywords:
  - sentence_bert_embedding
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - information_retrieval/retrieval_augmentation
  - natural_language_processing/sentence
name: Sentence-BERT for Sentence Embedding
date of note: 2024-12-07
---

## Concept Definition

>[!important]
>**Name**: Sentence-BERT for Sentence Embedding

>[!important] Definition
>The **Sentence-BERT (SBERT)** is an extension of BERT which is a pretrained language model that compute the *embedding representation* for an entire *sentence*.
>
>The  **Sentence-BERT (SBERT)** is described as below
>- *Required*: sentence $A$ and sentence $B$ as $$s_{A} := (w_{A}^{1}\,{,}\ldots{,}\,w_{A}^{m_{A}}), \quad s_{B}:= (w_{B}^{1}\,{,}\ldots{,}\,w_{B}^{m_{B}})$$
>- Both sentences pass through the **BERT** to compute *contextual word embedding* $$e_{A} := \text{BERT}(s_{A}) = (e_{A}^{1}\,{,}\ldots{,}\,e_{A}^{m_{A}}), \quad e_{B} := \text{BERT}(s_{B}) = (e_{A}^{1}\,{,}\ldots{,}\,e_{B}^{m_{B}})$$
>- Apply **pooling (maxPool / meanPool)** operation to derive a *fixed size* **sentence embedding** $$\begin{align*} u &= \text{Pool}(\text{BERT}(s_{A})) \\[5pt] v &= \text{Pool}(\text{BERT}(s_{B}))  \end{align*}$$ where $u,v\in \mathbb{R}^{d}$

- [[Contextual Embeddings and Word Sense]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Cosine Similarity and Cosine Distance]]
- [[Pooling for Deep Learning]]


>[!important] Definition
>The *fine-tuning* of **sentence-BERT** consists of the following tasks
>- **Classification**: 
>	- Consider the labeled dataset $$\mathcal{D}_{c} := \{ (s_{A,t}, s_{B,t}, y_{t}),\quad t=1\,{,}\ldots{,}\,T \}$$
>	- Combine both *sentence representations* $u,v$ and their *element-wise difference* $$x_{t} := (u_{t}, v_{t}, [u_{t}-v_{t}])$$
>	- Add a *feedfoward layer* and *softmax layer* to compute the logits $$o_{t} = \text{softmax}(W\,x_{t})$$ where the trainable weight is given by $$W\in \mathbb{R}^{k\times 3d}$$
>	- The loss function is the *cross-entropy* $$L(y_{t}, o_{t}) = -\sum_{t=1}^{T}y_{t}\log(o_{t})$$
>-  **Regression**: 
>	- Consider the labeled dataset $$\mathcal{D}_{c} := \{ (s_{A,t}, s_{B,t}, y_{t}),\quad t=1\,{,}\ldots{,}\,T \}$$
>	- Combine both *sentence representations* $u,v$  $$x_{t} := (u_{t}, v_{t})$$
>	- Compute the *cosine similarity* $$c_{t} := \left\langle  u_{t}\,,\, v_{t}   \right\rangle$$
>	- The loss function is the *mean squared error* $$L(y_{t}, c_{t}) = \sum_{t=1}^{T}\lVert y_{t} - \left\langle  u_{t}\,,\,v_{t}    \right\rangle \rVert $$
>- **Contrastive Learning**
>	- Consider the  *triplet pairs* with  *positive* and *negative* samples $$\mathcal{D}_{r} := \left\{ (s_{A,t}, s_{p,t}, s_{n,t}),\quad t=1\,{,}\ldots{,}\,T \right\} $$
>	- Compute the sentence embedding for each triplet pair as $$(u_{t}, v_{p,t}, v_{n,t})$$
>	- The loss function is the *triplet loss* $$L(u_{t}, v_{p,t}, v_{n,t}) := \max\left\{ \lVert u_{t} - v_{p,t} \rVert - \lVert u_{t} - v_{n, t} \rVert + \epsilon,\, 0 \right\} $$


- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Softmax Function and Log-Sum-Exp Function]]

- [[Siamese Network or Twin Tower Network for Contrastive Learning]]
- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Contrastive Learning]]

![[sentence_bert.png]]


## Explanation





-----------
##  Recommended Notes and References



- [[Representation Learning]]
- [[Masked Language Modeling as Language Model Training Task]]
- [[Next Sentence Prediction as Language Model Training Task]]

- [[Large Language Model and Pretrained Language Models]]


- [[Dense Text Retrieval with Pretrained Language Models]]
- [[Retrieval Augmented Generation]]
- [[Information Retrieval]]



- [[Speech and Language Processing by Jurafsky]]
- [[reimersSentenceBERTSentenceEmbeddings2019]] Nils Reimers and Iryna Gurevych. 2019. [Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://aclanthology.org/D19-1410). In _Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing (EMNLP-IJCNLP)_, pages 3982–3992, Hong Kong, China. Association for Computational Linguistics. 