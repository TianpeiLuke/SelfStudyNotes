---
tags:
  - concept
  - information_retrieval/retrieval_augmentation
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
keywords:
  - retrieval_augmented_generation
topics:
  - information_retrieval/retrieval_augmentation
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
name: Retrieval Augmented Generation
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Retrieval Augmented Generation

>[!important] Definition
>The method of *question answering* based on *retrieved documents* is called the **retrieval-augmented generation** or **RAG.**
>
>There are two stages for the *QA model* of *RAG*
>- **Retrieving Stage**: at this stage, we *retrieve* relevant *passages* from a text collection
>	- The component used in this stage is called the **retriever**;
>	- It is common to use **dense retriever** based on *masked language model*
>	- $$q \to [d_{1}\,{,}\ldots{,}\,d_{n}]$$
>- **Reading Stage**: at this stage, we *generate* answers *conditioned* on retrieved documents via **retrieval-augmented generation**.
>	- The text generator is based on *large language models*
>	- $$\{q,\, [d_{1}\,{,}\ldots{,}\,d_{n}]   \} \to a$$

- [[Question Answering Problem]]
- [[Information Retrieval]]
- [[Information Retrieval with Encoder Language Models]]
- [[Large Language Model and Pretrained Language Models]]

![[rag_question_answer_flow.png]]


![[rag_process.png]]

- Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. _arXiv preprint arXiv:2312.10997_.


- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]






## Explanation




## Paradigms of RAG



![[rag_paradigm.png]]

- Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. _arXiv preprint arXiv:2312.10997_.

## Variants of RAG System

![[rag_systems_2024.png]]

- Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. _arXiv preprint arXiv:2312.10997_.



## Compare with Other Learning

![[rag_icl_llm.png]]

- Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. _arXiv preprint arXiv:2312.10997_.

- [[In-Context Learning for LLM]]
- [[Prompt Engineering for LLM]]
- [[Parameter Efficient Fine Tuning or PEFT for Large Language Model]]



-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Foundational Models for Transfer Learning]]



- [[Generative Pre-trained Transformer or GPT]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


- Youtube
	- [Stanford CS25: V3 I Retrieval Augmented Language Models](https://www.youtube.com/watch?v=mE7IDf2SmJg)

- [[Speech and Language Processing by Jurafsky]] pp 302
- Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., ... & Kiela, D. (2020). Retrieval-augmented generation for knowledge-intensive nlp tasks. _Advances in Neural Information Processing Systems_, _33_, 9459-9474.  [[lewisRetrievalAugmentedGenerationKnowledgeIntensive2020]]
- Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., ... & Wang, H. (2023). Retrieval-augmented generation for large language models: A survey. _arXiv preprint arXiv:2312.10997_.
- Zhu, Y., Yuan, H., Wang, S., Liu, J., Liu, W., Deng, C., ... & Wen, J. R. (2023). Large language models for information retrieval: A survey. _arXiv preprint arXiv:2308.07107_.
