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

### ROUGE-N Score

>[!important] Definition
>Let $$w:=(w_{1}\,{,}\ldots{,}\,w_{T}), \quad v:=(v_{1}\,{,}\ldots{,}\,v_{S})$$ be the *output sequence* of language model, and the *reference ground truth*, respectively.
>
>The **Recall-Oriented Understudy for Gisting Evaluation (ROUGE)** is a *recall measure* on the *n-gram* of both the output sequence, and reference ground truth.
>
>Specifically, consider a set of *unique n-grams* of $w$ $$G_{n}(w) := \left\{ w_{1:n},\, w_{2:n+1}\,{,}\ldots{,}\, w_{T-n+1:T} \right\} $$
>- The set of *matched (overlapped) n-gram* is $$G_{n}(w) \cap G_{n}(v)$$
>- Define the **substring count** as the number of appearances of a string $s$ as a *substring* of $y$ $$C(s, y) := \#\left\{ i: s = y_{i:|s|+i-1} \right\} $$
>
>- The **ROUGE-N Precision** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\begin{align*}\text{ROUGE-Precision}(w, v; n) := \frac{\sum_{s\in G_{n}(w)\cap G_{n}(v)}C(s, w)}{\sum_{s\in G_{n}(w)}C(s, w)} = \frac{\sum_{s\in G_{n}(v)}C(s, w)}{\sum_{s\in G_{n}(w)}C(s, w)}\end{align*}$$
>	- Note that $$\sum_{s\in G_{n}(w)\cap G_{n}(v)}C(s, w) = \sum_{s\in G_{n}(v)}C(s, w)$$ is the *total count* of *overlapped n-gram* in candidate text with reference text.
>	- This includes all *repeated n-grams* in *matches*.
>	- The **ROUGE-n precision** counts *__all__ occurrences* of *overlapping n-grams* in the candidate text.
> 
>- The **ROUGE-N Recall** is computed as $$\begin{align*}\text{ROUGE-Recall}(w, v; n) := \frac{\sum_{s\in G_{n}(v)}\min\left\{ C(s, w), C(s, v) \right\}}{\sum_{s\in G_{n}(v)}C(s, v)}\end{align*}$$  
>	- $$\sum_{s\in G_{n}(w)\cap G_{n}(v)}\min\{C(s, w), C(s,v)\} = \sum_{s\in G_{n}(v)}\min\{C(s, w), C(s,v)\}$$
>	- Note that the numerator of the  **ROUGE-n recall** **limits** matches to the reference's *maximum count*.
>	- Similar to BLEU, it applies the **clipping** in numerator.
>- The **ROUGE-N F-measure** is given by $$\text{ROUGE-F}(w, v;n) := \frac{2\times\text{ROUGE-Recall}\times \text{ROUGE-Precision} }{\text{ROUGE-Recall}  + \text{ROUGE-Precision} }$$

- [[n-Gram Model and Language Model]]
- [[Bilingual Evaluation Understudy or BLEU metric for LLM Generation]]
- [[Recall and Precision and F-Measure]]

>[!info]
>If the candidate text overgenerates repeated n-grams that are present in the reference, the **ROUGE-Precision** will count them as matches, potentially **inflating** the score. 
>
>In contrast, the **ROUGE Recall** do **not inflate the recall score** due to clipping.

### ROUGE-L based on the Longest Common Subsequence

>[!important] Definition
>Let $$w:=(w_{1}\,{,}\ldots{,}\,w_{T}), \quad v:=(v_{1}\,{,}\ldots{,}\,v_{S})$$ be the *output sequence* of language model of length $T$, and the *reference ground truth* of length $S$, respectively.
>
>Specifically, consider the *longest common subsequence* between $w$ and $v$ as $$\text{LCS}(w, v)$$
>
>Then
>- the **ROUGE-L Precision** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\text{ROUGE-L Precision}(w, v) := \frac{\text{LCS}(w, v)}{T}$$
>- The **ROUGE-L Recall** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\text{ROUGE-L Recall}(w, v) := \frac{\text{LCS}(w, v)}{S}$$
>- The **ROUGE-L** or **ROUGE-L F measure** is given by $$\begin{align*}\text{ROUGE-L}(w,v; \beta) &:= \text{ROUGE-L F}(w, v; \beta) \\[8pt] &:= \frac{(1 + \beta^2)\times \text{ROUGE-L Precision}\times \text{ROUGE-L Recall}}{\text{ROUGE-L Precision} + \beta^2\;\text{ROUGE-L Recall}}\end{align*}$$
>	- The **ROUGE-L F measure** is called the **ROUGE-L score.**

- [[Recall and Precision and F-Measure]]

### ROUGE-S based on the Skip-Bigram Co-Occurrence

>[!important] Definition
>**Skip-bigram** is *any pair* of words in their *sentence order*, allowing for *arbitrary gaps*.
>- For instance, a sentence of 4 words has $4 \choose 2$ skip-bigrams.
>  
>Let $$w:=(w_{1}\,{,}\ldots{,}\,w_{T}), \quad v:=(v_{1}\,{,}\ldots{,}\,v_{S})$$ be the *output sequence* of language model, and the *reference ground truth*, respectively.  
>- Denote $$\text{Skip-2}(w, v)$$ be the *total count* of *overlapped skip-bigram* between $w$ and $v$
>  
>Then  
>- the **ROUGE-S Precision** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\text{ROUGE-S Precision}(w, v) := \frac{\text{Skip-2}(w, v)}{T \choose 2}$$
>- The **ROUGE-S Recall** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\text{ROUGE-S Recall}(w, v) := \frac{\text{Skip-2}(w, v)}{S \choose 2}$$  
>- The  **ROUGE-S**  or **ROUGE-S F measure** is given by $$\begin{align*}\text{ROUGE-S}(w,v; \beta) &:= \text{ROUGE-S F}(w, v; \beta) \\[8pt] &:= \frac{(1 + \beta^2)\times \text{ROUGE-S Precision}\times \text{ROUGE-S Recall}}{\text{ROUGE-S Precision} + \beta^2\;\text{ROUGE-S Recall}}\end{align*}$$

- [[Co-Occurrence Matrix]]


## Explanation

>[!important]
>- **ROUGE-N** is often used to evaluate the *grammatical correctness* and *fluency* of generated text.
>- **ROUGE-L** is often used to evaluate the *semantic similarity* and *content coverage* of generated text, as it considers the common subsequence regardless of *word order*.
>- **ROUGE-S** is often used to evaluate the *coherence and local cohesion* of generated text, as it captures the *semantic similarity* between adjacent words.


### BLEU vs. ROUGE

>[!info]
>- **BLUE** is **precision**-based metrics
>- **ROUGE** is **recall**-based metrics

- [[Recall and Precision and F-Measure]]
- [[Bilingual Evaluation Understudy or BLEU metric for LLM Generation]]

>[!info]
>- $$\text{ROUGE Precision} = \frac{\text{Number of overlapping n-grams}}{\text{Total n-grams in generated text}}$$
>- $$\text{Modified n-Gram Precision} = \frac{\text{Clipped Count of overlapping n-grams}}{\text{Total n-grams in generated text}}$$​

| Aspect                    | ROUGE Precision                  | Modified n-Gram Precision (BLEU)                      |
| ------------------------- | -------------------------------- | ----------------------------------------------------- |
| **Primary Use**           | Summarization                    | Machine translation                                   |
| **Focus**                 | Coverage of the reference text   | Accuracy of generated text                            |
| **N-Gram Counting**       | Counts *all* overlapping n-grams | Counts overlapping n-grams with *clipping*            |
| **Brevity Consideration** | Does not penalize for brevity    | *Penalizes for brevity* (via brevity penalty in BLEU) |
| **Orientation**           | **Recall/Precision balance**     | **Precision-focused**                                 |

>[!quote]
>In summary,
>- while **ROUGE precision** is *simpler* and mainly about overlap, 
>- **BLEU's modified precision** introduces **clipping** to ensure *fidelity* and *penalizes excessive repetition* or unfaithful generation.


## Application: LLM Performance Measure

>[!important]
>**ROUGE score** is mainly used for **text summarization.**


### Text Summarization

- [[Text Summarization]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Large Language Model and Pretrained Language Models]]


-----------
##  Recommended Notes



- Wikipedia [ROUGE_(metric)](https://en.wikipedia.org/wiki/ROUGE_(metric))

- [[Speech and Language Processing by Jurafsky]]
- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]

- [[Practical Natural Language Processing by Vajjala]] pp 69 - 70
- Chin-Yew Lin. 2004. [ROUGE: A Package for Automatic Evaluation of Summaries](https://aclanthology.org/W04-1013). In _Text Summarization Branches Out_, pages 74–81, Barcelona, Spain. Association for Computational Linguistics.