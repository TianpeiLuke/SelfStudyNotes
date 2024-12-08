---
tags:
  - concept
  - natural_language_processing/sequence_classification
  - natural_language_processing/sequence_pair_classification
keywords:
  - sequence_classification
  - sequence_pair_classification
topics:
  - natural_language_processing/sequence_pair_classification
  - natural_language_processing/sequence_classification
name: Sequence Classification and Sequence-Pair Classification
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Sequence Classification and Sequence-Pair Classification

>[!important] Definition
>The task of **sequence classification** or **text classification** is to classify an *entire sequence of text* with a *single label*.
>$$
>(w_{1}\,{,}\ldots{,}\,w_{T}) \to y\in \mathcal{Y}
>$$

^eebd31

- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Classification Problem]]

>[!important] Definition
>Another important type of problem involves the *classification of pairs* of input sequences, i.e. **sequence-pair classification** task.
>$$
> \{ (w_{1}\,{,}\ldots{,}\,w_{T}),\, (v_{1}\,{,}\ldots{,}\,v_{S}) \} \to y\in \mathcal{Y}
>$$
>
>Application of sequence-pair classification includes
>- *paraphrase detection*, 
>- *logical entailment*, 
>- and *discourse coherence*
>  

^107cfe


## Explanation

>[!info]
>**Sequence classification** and **sequence-pair classification** follow a "*many-to-one*" architecture.
>

![[rnn_sequence_one_sequence.png]]


- [[Encoder-Decoder Sequence-to-Sequence Architecture]]

## Models


- [[Multinomial Naive Bayes Model]]
- [[Support Vector Machine Kernel Expansion and RKHS]]
- [[Positive Definite Kernel Examples]]

- [[Probabilistic Graphical Models]]

- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Gated Recurrent Units in Neural Network]]


- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]



## Examples

### Text Classification

- [[Sentiment Analysis]]

### Sequence-Pair Classification

- [[Next Sentence Prediction as Language Model Training Task]]
- [[Discourse Coherence]]
- [[Natural Language Inference or Textual Entailment]]




-----------
##  Recommended Notes and References





- [[Speech and Language Processing by Jurafsky]] pp 235 - 236