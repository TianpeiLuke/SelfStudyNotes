---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords: 
topics: 
name: Masked Language Modeling as Language Model Training Task
date of note: 2024-11-27
---

## Concept Definition

>[!important]
>**Name**: Masked Language Modeling as Language Model Training Task

>[!important] Definition
>One of two tasks to training BERT is called **Masked Language  Modeling (MLM)**.
>- It is a *self-supervised task*, where the *training corpus* contains a large amount of *unannotated text*.
>
>In **MLM**, the model 


- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Large Language Model and Pretrained Language Models]]
- [[Self-Supervised Training of Large Language Model and Teacher Forcing]]

## Explanation

>[!quote]
>The **first token** of every input string is given by a special token `<class>`, and the corresponding *output* of the model is *ignored* during pre-training. 
>- Its role will become apparent when we discuss *fine-tuning*. 
>
>The model is pre-trained by presenting token sequences at the input. 
>- A *randomly chosen subset* of the tokens, say $15\%$, are *replaced* with a special token denoted `<mask>`. 
>- The model is trained to *predict the missing tokens* at the corresponding output nodes. 
>- This is analogous to the masking used in **word2vec** to learn *word embeddings*.
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 388  



-----------
##  Recommended Notes and References


- [[liuRoBERTaRobustlyOptimized2019]]
- [[devlinBERTPretrainingDeep2019]]

- [[Speech and Language Processing by Jurafsky]] pp 226 - 228
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1052