---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - rouge_metric_nlp
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: ROUGE metric for LLM Generation
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: ROUGE metric for LLM Generation

>[!important] Definition
>The **ROUGE metric** or the **Recall-Oriented Understudy for Gisting Evaluation** is a set of metrices and software package used for evaluation of *text summarization* and *mature translation.*

![[Bilingual Evaluation Understudy or BLEU metric for LLM Generation#^c36fe8]]

>[!important] Definition
>Let $$w:=(w_{1}\,{,}\ldots{,}\,w_{T}), \quad v:=(v_{1}\,{,}\ldots{,}\,v_{S})$$ be the *output sequence* of language model, and the *reference ground truth*, respectively.
>
>The **Recall-Oriented Understudy for Gisting Evaluation (ROUGE)** is a *recall measure* on the *n-gram* of both the output sequence, and reference ground truth.
>
>Specifically, consider a set of *n-grams* of $w$ $$G_{n}(w) := \left\{ w_{1:n},\, w_{2:n+1}\,{,}\ldots{,}\, w_{T-n+1:T} \right\} $$
>- Define the **substring count** as the number of appearances of a string $s$ as a *substring* of $y$ $$C(s, y) := \#\left\{ i: s = y_{i:|s|+i-1} \right\} $$
>
 The **ROUGE-n** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows:
>$$
>\begin{align*}
>\text{ROUGE}(w, v; n) := \frac{\sum_{s\in G_{n}(v)}\min\left\{C(s, w),\,C(s, v)  \right\}}{\sum_{s\in G_{n}(v)}C(s, v)}
>\end{align*}
>$$
>- The *denominator* is the *total count* of $n$-gram of *reference* $v$ in the *reference sequence* $v$; (which acts as the *predicted positive*) $$\text{P } := \sum_{s\in G_{n}(v)}C(s, v)$$
>- The *numerator* is the *maximum reference count* of *candidate* $n$-gram in *reference sequence* $v$; (which acts as the *true positive*)  $$\text{TP } := \sum_{s\in G_{n}(v)}C(s, w)$$
>- The *normalize* the metric, the numerator need to be **clipped** by  *total count* of $n$-gram of *candidate* $w$ in the *candidate sequence* $w$ $$\text{TP } := \sum_{s\in G_{n}(v)}\min\{C(s, v), C(s, w)  \}$$

- [[n-Gram Model and Language Model]]
- [[Bilingual Evaluation Understudy or BLEU metric for LLM Generation]]
- [[Recall and Precision and F-Measure]]

>[!important] Definition
>Let $$S_{w} := \{ w^{(1)} \,{,}\ldots{,}\, w^{(N)} \}, \text{ where }  w^{(i)}:=(w_{1}^{(i)}\,{,}\ldots{,}\,w_{T}^{(i)})$$ be a set of $N$ *output sequences* of language model,  
>- and let $$S_{v}^{(i)} := \{ v^{(1,i)} \,{,}\ldots{,}\, v^{(M,i)} \}, \text{ where }  v^{(j,i)}:=(v_{1}^{(j,i)}\,{,}\ldots{,}\,v_{S}^{(j,i)})$$  be a set of $M$ *reference ground truth* for *each output sequence* $w^{(i)}$.
>- Denote the total reference set $$S_{v} := \left\{ S_{v}^{(1)} \,{,}\ldots{,}\, S_{v}^{(N)}\right\} $$
>
>
>The **ROUGE-n** between the candidate set $S_{w}$ and  reference set $S_{v}$ is computed as follows:
>$$
>\begin{align*}
>p_{n}(S_{w}, S_{v}) := \frac{\sum_{i=1}^{N}\sum_{s\in G_{n}(w)}\min\left\{C(s, w^{(i)}),\; \max_{v^{(j,i)}\in S_{v}^{(i)}}C(s, v^{(j,i)})  \right\}}{\sum_{i=1}^{N}\sum_{s\in G_{n}(w)}C(s, w^{(i)})}
>\end{align*}
>$$


### ROUGE-L based on the Longest Common Subsequence





## Explanation



>[!info]
>- **BLUE** is **precision**-based metrics
>- **ROUGE** is **recall**-based metrics

- [[Recall and Precision and F-Measure]]


## Application: LLM Performance Measure


### Machine Translation

- [[Machine Translation]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Large Language Model and Pretrained Language Models]]

### Text Summarization

- [[Text Summarization]]
- [[Generative Pre-trained Transformer or GPT]]



-----------
##  Recommended Notes



- Wikipedia [ROUGE_(metric)](https://en.wikipedia.org/wiki/ROUGE_(metric))

- [[Speech and Language Processing by Jurafsky]]
- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]

- [[Practical Natural Language Processing by Vajjala]] pp 69 - 70
- Chin-Yew Lin. 2004. [ROUGE: A Package for Automatic Evaluation of Summaries](https://aclanthology.org/W04-1013). In _Text Summarization Branches Out_, pages 74–81, Barcelona, Spain. Association for Computational Linguistics.