---
tags:
  - concept
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - natural_language_processing/sequence_classification
  - natural_language_processing/sequence_pair_classification
keywords:
  - fine_tuning_bert
  - sequence_classification
  - sequence_pair_classification
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
name: Fine-Tuning for Sequence or Sequence-Pair Classification via BERT
date of note: 2024-11-28
---

## Concept Definition

>[!important]
>**Name**: Fine-Tuning for Sequence or Sequence-Pair Classification via BERT

![[Pre-Training and Fine-Tuning Paradigm for Transfer Learning#^7e9176]]

![[Pre-Training and Fine-Tuning Paradigm for Transfer Learning#^036480]]

>[!important] Definition
>In order to **fine-tune** masked language models such as BERT, we add *application-specific* circuitry, called a special **head** on top of pre-trained models, taking their output as input.
>- The **fine-tuning process** consists of using labeled data about the application to train these additional *application-specific parameters*.
>- Typically, the fine-tuning would *freeze* or *make minimal adjustments* to the pretrained language models.

- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]
- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


### Sequence Classification or Text Classification

![[Sequence Classification and Sequence-Pair Classification#^eebd31]]

- [[Sequence Classification and Sequence-Pair Classification]]
- [[Classification Problem]]
- [[Encoder-Decoder Sequence-to-Sequence Architecture]]

>[!important] Definition
>In **sequence classification**, we represent an entire sequence to be classified as a single vector.
>- One way is to represent it as the *sum* of all *token embeddings* in the sequence.
>- In *BERT*, we add a new **unique special token** `[CLS]` and *prepend* it to the *start* of all input sequences.
>	- We do this both in *pretraining* and *fine-tuning*
>	- The *output vector* corresponding to `[CLS]` represents the *entire sequence*. $$h_{L}^{CLS} \in \mathbb{R}^{d}$$
>	- Then this vector is the input of the **classification head**, which is a *logistic regression* or *neural network*. For instance, $$\hat{y} = \text{softmax}(W_{C}\,h_{L}^{CLS})$$ where $$W_{C}\in \mathbb{R}^{|\mathcal{Y}|\times d}$$
>	- To *fine-tune* $W_{C}$, we need supervised training data with input sequence and output labels. Then we use *cross-entropy loss* as objective. $$L_{CE}(y, \hat{y}) = \frac{1}{N}\sum_{i=1}^{N}y_{i}\;\log \hat{y}_{y=y_{i}}$$
>	- Note that this *classification loss* can be used to update *both* $W_{C}$ and *weight parameters* in *pre-trained models.* 
>	- In practice, reasonable classification performance is typically achieved with *only minimal changes* to the language  model parameters, often limited to updates over the *final few layers of the transformer*.

- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Masked Language Modeling as Language Model Training Task]]

- [[Logistic Regression]]
- [[Softmax Function and Log-Sum-Exp Function]]

![[sequence_classification_bert.png]]

### Sequence-Pair Classification

![[Sequence Classification and Sequence-Pair Classification#^107cfe]]

- [[Sequence Classification and Sequence-Pair Classification]]
- [[Next Sentence Prediction as Language Model Training Task]]
- [[Natural Language Inference or Textual Entailment]]
- [[Discourse Coherence]]

>[!important] Definition
>During the *fine-tuning* for **sequence-pair classification**, pairs of labeled sentences from a supervised fine-tuning set are presented to the model.
>- The model produce a vector $h_{L}^{CLS}$ for the *prepended* `[CLS]` token for the sequence-pair.
>- Two input sentences are separated by `[SEP]`


![[next_sentence_prediction_loss.png]]


## Explanation

>[!info]
>**Sequence classification** and **sequence-pair classification** follow a "*many-to-one*" architecture.
>


![[rnn_sequence_one_sequence.png]]

>[!quote]
>- When data for task $A$ is very **scarce**, we might simply **re-train** the *final layer* of the network. 
>- In contrast, if there are more data points, it is feasible to *retrain several layers*. 
>- The process of learning parameters using one task that are then applied to one or more other tasks is called **pre-training**. 
>	- Note that for the new task, instead of applying stochastic gradient descent to the whole network, it is much more efficient to send the new training data *once* through the *fixed pre-trained network* so as to evaluate the training inputs in the new representation. 
>	- Iterative gradient-based optimization can then be applied just to the *smaller network* consisting of the *final layers*. 
>- As well as using a pre-trained network as a fixed pre-processor for a different task, it is also possible to apply **fine-tuning** in which the whole network is adapted to the data for task $A$. 
>	- This is generally done with a very *small learning rate* for a *limited number of iterations* to ensure that the network does not over-fit to the relatively small data set available for the new task.
>	  
>-- [[Speech and Language Processing by Jurafsky]] pp 189 - 190	  


- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]
- [[Transfer Learning]]
- [[Foundational Models for Transfer Learning]]

## Applications

### Sentiment Analysis

- [[Sentiment Analysis]]

### Discourse Coherence

- [[Discourse Coherence]]


### Natural Language Inference

- [[Natural Language Inference or Textual Entailment]]






-----------
##  Recommended Notes and References


- [[Multi-modal BERT Classification Model v1 for BSM]]
- [[Trainer for BERT Fine-tune Classification in BSM]]



- [[Speech and Language Processing by Jurafsky]] pp 234 - 236
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1041
- [[Deep Learning Foundations and Concepts by Bishop]] pp 3, 22, 189, 392