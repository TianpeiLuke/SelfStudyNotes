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
>The **Bilingual Evaluation Understudy (BLEU)** is an algorithm that measures the quality of text based on the *amount of $n$-gram overlap* between the *output sentence* of language model and the *reference ground truth*.

### Modified $n$-Gram Precision

>[!important] Definition
>Let $$w:=(w_{1}\,{,}\ldots{,}\,w_{T}), \quad v:=(v_{1}\,{,}\ldots{,}\,v_{S})$$ be the *output sequence* of language model, and the *reference ground truth*, respectively.
>
>The **Bilingual Evaluation Understudy (BLEU)** is a *precision measure* on the *n-gram* of both the output sequence, and reference ground truth.
>
>Specifically, consider a set of *unique n-grams* of $w$ $$G_{n}(w) := \left\{ w_{1:n},\, w_{2:n+1}\,{,}\ldots{,}\, w_{T-n+1:T} \right\} $$
>- Define the **substring count** as the number of appearances of a string $s$ as a *substring* of $y$ $$C(s, y) := \#\left\{ i: s = y_{i:|s|+i-1} \right\} $$
>
 The **modified n-gram precision** between one candidate sequence $w$ and one reference sequence $v$ is computed as follows:
>$$
>\begin{align*}
>p_{n}(w, v) := \frac{\sum_{s\in G_{n}(w)}\min\left\{C(s, w),\,C(s, v)  \right\}}{\sum_{s\in G_{n}(w)}C(s, w)}
>\end{align*}
>$$
>- The *denominator* is the *total count* of *candidate* $n$-gram; (which acts as the *predicted positive*) $$\text{PP } := \sum_{s\in G_{n}(w)}C(s, w)$$
>- The *numerator* is the *total count of overlapped candidate* $n$-gram with reference set; (which acts as the *true positive*)  $$\text{TP } := \sum_{s\in G_{n}(v)}C(s, w) = \sum_{s\in G_{n}(w) \cap G_{n}(v)}C(s, w)$$
>- The *normalize* the metric, the numerator is **clipped** as *total count* of *overlapped candidate* $n$-gram but not exceeding the corresponding count in reference set   $$\text{TP } := \sum_{s\in G_{n}(w)}\min\{C(s, v), C(s, w)  \} = \sum_{s\in G_{n}(w) \cap G_{n}(v)}\min\{C(s, v), C(s, w)  \}$$

^c36fe8

- [[n-Gram Model and Language Model]]
- [[Recall and Precision and F-Measure]]

>[!quote]
>We formalize this intuition as the **modified unigram precision**. 
>
>To compute this, 
>- one first counts the *maximum* number of times a word *occurs* in any *single reference* translation. 
>- Next, one *clips* the *total count* of each candidate word by its *maximum reference count*,
>- *adds* these clipped counts up, 
>- and *divides* by the *total (unclipped) number* of candidate words.
>
>...
>
>**Modified n-gram precision** is computed similarly for any $n$: 
>- all candidate *n-gram counts* and their corresponding *maximum reference counts* are collected. 
>- The candidate counts are *clipped* by their corresponding *reference maximum value*, 
>- summed, 
>- and *divided* by the *total number* of candidate n-grams.
>  
>-- Papineni, K., Roukos, S., Ward, T., & Zhu, W. J. (2002, July). Bleu: a method for automatic evaluation of machine translation. In _Proceedings of the 40th annual meeting of the Association for Computational Linguistics_ (pp. 311-318).

>[!info]
>$$
>\begin{align*}
>\sum_{s\in G_{n}(w)}\min\{ C(s, w), C(s, v) \} &= \sum_{s\in G_{n}(w) \cap G_{n}(v)}\min\{ C(s, w), C(s, v) \} \\[5pt] 
>&= \sum_{s\in G_{n}(v)}\min\{ C(s, w), C(s, v) \}
>\end{align*}
>$$

### Modified $n$-Gram Precision for Blocks of Text

>[!important] Definition
>Let $$S_{w} := \{ w^{(1)} \,{,}\ldots{,}\, w^{(N)} \}, \text{ where }  w^{(i)}:=(w_{1}^{(i)}\,{,}\ldots{,}\,w_{T}^{(i)})$$ be a set of $N$ *output sequences* of language model,  
>- and let $$S_{v}^{(i)} := \{ v^{(1,i)} \,{,}\ldots{,}\, v^{(M,i)} \}, \text{ where }  v^{(j,i)}:=(v_{1}^{(j,i)}\,{,}\ldots{,}\,v_{S}^{(j,i)})$$  be a set of $M$ *reference ground truth* for *each output sequence* $w^{(i)}$.
>- Denote the total reference set $$S_{v} := \left\{ S_{v}^{(1)} \,{,}\ldots{,}\, S_{v}^{(N)}\right\} $$
>
>
>The **modified n-gram precision** between the candidate set $S_{w}$ and  reference set $S_{v}$ is computed as follows:
>$$
>\begin{align*}
>p_{n}(S_{w}, S_{v}) := \frac{\sum_{i=1}^{N}\sum_{s\in G_{n}(w^{(i)})}\min\left\{C(s, w^{(i)}),\; \max_{v^{(j,i)}\in S_{v}^{(i)}}C(s, v^{(j,i)})  \right\}}{\sum_{i=1}^{N}\sum_{s\in G_{n}(w^{(i)})}C(s, w^{(i)})}
>\end{align*}
>$$

>[!important]
>The modified n-gram precision unduly gives a high score for candidate strings that are "**telegraphic**", that is, containing *all* the n-grams of the *reference strings*, but for *as few times as possible*.


### Brevity Penalty

>[!important] Definition
>The **brevity penalty** punish the output sequence that is *too short*, which is defined as 
>$$
>\begin{align*}
>\text{BP}(S_{w}, S_{v}) &:= \exp \left(- \left[ \frac{r}{c} - 1\right]_{+}\right) \\[5pt]
>&= \left\{\begin{array}{cl} \exp\left( 1 - \dfrac{r}{c} \right) & \text{if }  c \le r \\[8pt] 1 & \text{if }c > r \end{array}  \right. 
>\end{align*}
>$$
>where 
>- the exponent is the *positive part*  $$\left[ \frac{r}{c} -1 \right]_{+} = \max\left\{ 0,  \frac{r}{c} -1 \right\}  $$
>- and $c$ is the **total length of candidate corpus** $$c:= \sum_{i=1}^{N}|w^{(i)}|$$
>- and $r$ is the **effective reference corpus length** $$r:= \sum_{i=1}^{N}|v^{(j^{*},i)}|$$ and $$v^{(j^{*},i)} := \arg\min_{v^{(j,i)}\in S_{v}^{(i)}}\lvert |v^{(j,i)}| - |w^{(i)}| \rvert $$ is the reference sequence whose length is closest to the candidate sequence.

- [[Hinge Loss as Surrogate Loss Function]]


### BLEU Score

>[!important] Definition
>Let $$S_{w} := \{ w^{(1)} \,{,}\ldots{,}\, w^{(N)} \}, \text{ where }  w^{(i)}:=(w_{1}^{(i)}\,{,}\ldots{,}\,w_{T}^{(i)})$$ be a set of $N$ *output sequences* of language model,  
>- and let $$S_{v}^{(i)} := \{ v^{(1,i)} \,{,}\ldots{,}\, v^{(M,i)} \}, \text{ where }  v^{(j,i)}:=(v_{1}^{(j,i)}\,{,}\ldots{,}\,v_{S}^{(j,i)})$$  be a set of $M$ *reference ground truth* for *each output sequence* $w^{(i)}$.
>- Denote the total reference set $$S_{v} := \left\{ S_{v}^{(1)} \,{,}\ldots{,}\, S_{v}^{(N)}\right\} $$
>  
>Define a set of normalized weights $\alpha$ for $n$ as $$\sum_{n=1}^{\infty}\alpha_{n} = 1, \quad \alpha_{n} >0, \forall n=1\,{,}\ldots{,}\,$$  
>
>The **BLEU score** associated with weights $\alpha$  between the candidate set $S_{w}$ and  reference set $S_{v}$ is computed as follows:
>$$
>\text{BLEU}_{\alpha}(S_{w}; S_{v}) := \text{BP}(S_{w}, S_{v}) \times \exp \left(\sum_{n=1}^{\infty}\alpha_{n}\,p_{n}(S_{w}, S_{v})\right)
>$$
>- This is the **weighted geometric mean** of *all modified n-gram precisions*, *multiplied* by *brevity penalty.* .





## Explanation

>[!info]
>- **BLUE** is **precision**-based metrics
>- **ROUGE** is **recall**-based metrics

- [[Recall and Precision and F-Measure]]
- [[ROUGE metric for LLM Generation]]


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
- Papineni, K., Roukos, S., Ward, T., & Zhu, W. J. (2002, July). Bleu: a method for automatic evaluation of machine translation. In _Proceedings of the 40th annual meeting of the Association for Computational Linguistics_ (pp. 311-318).