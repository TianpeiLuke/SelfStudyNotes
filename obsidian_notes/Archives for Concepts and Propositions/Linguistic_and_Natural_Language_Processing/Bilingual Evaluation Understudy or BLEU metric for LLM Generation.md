---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - blue_metric_nlp
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Bilingual Evaluation Understudy or BLEU metric for NLP System
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: Bilingual Evaluation Understudy or BLEU metric for NLP System

>[!important] Definition
>The **Bilingual Evaluation Understudy (BLUE)** is an algorithm that measures the quality of text based on the *amount of $n$-gram overlap* between the *output sentence* of language model and the *reference ground truth*.


- [[n-Gram Model and Language Model]]
- [[Jaccard Similarity and Jaccard Distance between Two Sets]]


## Explanation

>[!info]
>- **BLUE** is **precision**-based metrics
>- **ROUGE** is **recall**-based metrics

- [[Recall and Precision and F-Measure]]
- [[ROUGE metric for LLM Generation]]


## Application: LLM Performance Measure

### Machine Translation

>[!info]
>**BLUE** metrics are mainly used in **machine translation**.

- [[Machine Translation]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Large Language Model and Pretrained Language Models]]

### Text Summarization

>[!info]
>Even though **BLEU** and **METEOR** are good metrics for machine translation, they *may not* be good metrics when applied to other generation tasks. 
>- For example, in the case of **dialog generation**, the *ground truth* is one of the correct answers, but there could be *many variations* in responses that are not listed. 
>- In cases like this, **precision-based metrics** such as BLEU and METEOR will completely fail to capture the task performance faithfully.

- [[Text Summarization]]
- [[Generative Pre-trained Transformer or GPT]]



-----------
##  Recommended Notes





- [[Speech and Language Processing by Jurafsky]]
- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]

- Wikipedia [BLEU](https://en.wikipedia.org/wiki/BLEU)

- [[Practical Natural Language Processing by Vajjala]]  pp 69 - 70