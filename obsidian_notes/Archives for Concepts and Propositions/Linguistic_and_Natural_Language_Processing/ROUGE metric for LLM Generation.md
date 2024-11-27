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
>Specifically, consider a set of *unique n-grams* of $w$ $$G_{n}(w) := \left\{ w_{1:n},\, w_{2:n+1}\,{,}\ldots{,}\, w_{T-n+1:T} \right\} $$
>- Define the **substring count** as the number of appearances of a string $s$ as a *substring* of $y$ $$C(s, y) := \#\left\{ i: s = y_{i:|s|+i-1} \right\} $$
>
>- The **ROUGE-n precision** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows: $$\begin{align*}\text{ROUGE-n-Precision}(w, v; n) := \frac{\sum_{s\in G_{n}(w)\cap G_{n}(v)}C(s, w)}{\sum_{s\in G_{n}(w)}C(s, w)} = \frac{\sum_{s\in G_{n}(v)}C(s, w)}{\sum_{s\in G_{n}(w)}C(s, w)}\end{align*}$$
>	- Note that $$\sum_{s\in G_{n}(w)\cap G_{n}(v)}C(s, w) = \sum_{s\in G_{n}(v)}C(s, w)$$ is the *total count* of *overlapped n-gram* in candidate text with reference text.
>	- This includes all *repeated n-grams* in *matches*.
>	- The **ROUGE-n precision** counts *__all__ occurrences* of *overlapping n-grams* in the candidate text.
> 
>- The **ROUGE-n recall** is computed as $$\begin{align*}\text{ROUGE-n-Recall}(w, v; n) := \frac{\sum_{s\in G_{n}(v)}\min\left\{ C(s, w), C(s, v) \right\}}{\sum_{s\in G_{n}(v)}C(s, v)}\end{align*}$$  
>	- $$\sum_{s\in G_{n}(w)\cap G_{n}(v)}\min\{C(s, w), C(s,v)\} = \sum_{s\in G_{n}(v)}\min\{C(s, w), C(s,v)\}$$
>	- Note that the numerator of the  **ROUGE-n recall** **limits** matches to the reference's *maximum count*.
>	- Similar to BLEU, it applies the **clipping** in numerator.
>- The **ROUGE-n F-measure** is given by $$\text{ROUGE-n-F}(w, v;n) := \frac{2\times\text{ROUGE-n-Recall}\times \text{ROUGE-n-Precision} }{\text{ROUGE-n-Recall}  + \text{ROUGE-n-Precision} }$$

- [[n-Gram Model and Language Model]]
- [[Bilingual Evaluation Understudy or BLEU metric for LLM Generation]]
- [[Recall and Precision and F-Measure]]

>[!important] Definition
>Let $$S_{w} := \{ w^{(1)} \,{,}\ldots{,}\, w^{(N)} \}, \text{ where }  w^{(i)}:=(w_{1}^{(i)}\,{,}\ldots{,}\,w_{T}^{(i)})$$ be a set of $N$ *output sequences* of language model,  
>- and let $$S_{v}^{(i)} := \{ v^{(1,i)} \,{,}\ldots{,}\, v^{(M,i)} \}, \text{ where }  v^{(j,i)}:=(v_{1}^{(j,i)}\,{,}\ldots{,}\,v_{S}^{(j,i)})$$  be a set of $M$ *reference ground truth* for *each output sequence* $w^{(i)}$.
>- Denote the total reference set $$S_{v} := \left\{ S_{v}^{(1)} \,{,}\ldots{,}\, S_{v}^{(N)}\right\} $$
>
>
>The **ROUGE-n Recall** between the candidate set $S_{w}$ and  reference set $S_{v}$ is computed as follows:
>- $$\begin{align*}\text{ROUGE-n-Precision}(S_{w}, S_{v}) := \frac{\sum_{i=1}^{N}\sum_{j=1}^{M}\sum_{s\in G_{n}(v^{(j,i)})}C(s, w^{(i)})}{\sum_{i=1}^{N}\sum_{s\in G_{n}(w^{(i)})}C(s, w^{(i)})}\end{align*}$$
>- $$\begin{align*}\text{ROUGE-n-Recall}(S_{w}, S_{v}) := \frac{\sum_{i=1}^{N}\sum_{j=1}^{M}\sum_{s\in G_{n}(v^{(j,i)})}\min\left\{C(s, w^{(i)}),\; \max_{v^{(j,i)}\in S_{v}^{(i)}}C(s, v^{(j,i)})  \right\}}{\sum_{i=1}^{N}\sum_{j=1}^{M}\sum_{s\in G_{n}(v^{(j,i)})}C(s, v^{(j,i)})}\end{align*}$$

>[!important] Definition
>Define a set of normalized weights $\alpha$ for $n$ as $$\sum_{n=1}^{\infty}\alpha_{n} = 1, \quad \alpha_{n} >0, \forall n=1\,{,}\ldots{,}\,$$  
>
>The **ROUGE score** is given by the weighted sum of *ROUGE recall*
>$$
>\text{ROUGE}(S_{w}, S_{v}) := \sum_{n=1}^{\infty}\alpha_{n}\;\text{ROUGE-n-Recall}(S_{w}, S_{V})
>$$


### ROUGE-L based on the Longest Common Subsequence





## Explanation

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

>[!info]
>**ROUGE score** is mainly used for **text summarization.**


### Text Summarization

- [[Text Summarization]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]



-----------
##  Recommended Notes



- Wikipedia [ROUGE_(metric)](https://en.wikipedia.org/wiki/ROUGE_(metric))

- [[Speech and Language Processing by Jurafsky]]
- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]

- [[Practical Natural Language Processing by Vajjala]] pp 69 - 70
- Chin-Yew Lin. 2004. [ROUGE: A Package for Automatic Evaluation of Summaries](https://aclanthology.org/W04-1013). In _Text Summarization Branches Out_, pages 74–81, Barcelona, Spain. Association for Computational Linguistics.