---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/models
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
keywords:
  - bert_transformer
topics:
  - deep_learning/models
  - natural_language_processing/large_language_models
name: Bidirectional Encoder Representation from Transformer or BERT
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Bidirectional Encoder Representation from Transformer or BERT


### Encoder-Only Transformer Architecture

#### Unmasked Attention 

![[Attention Mechanism in Neural Network#^332141]]

![[causal_and_masked_matrix.png]]

![[causal_and_masked_transformer.png]]

- [[Attention Mechanism in Neural Network]]

>[!quote]
>The term ‘**bidirectional**’ refers to the fact that the network sees words *both before and after* the *masked word* and can use both sources of information to make a prediction. 
>
>As a consequence, unlike **decoder models**, there is *no need* to *shift* the inputs to the *right by one place*, and there is no need to *mask* the outputs of each layer from seeing input tokens occurring later in the sequence. 
>- Compared to the decoder model, an encoder is **less efficient** since *only a fraction* of the sequence tokens are used as training labels. 
>- Moreover, an encoder model is *unable to generate sequences*.

- [[Large Language Model and Pretrained Language Models]]
- [[Generative Pre-trained Transformer or GPT]]

![[bert_architecture.png]]

- [[Transformer Network]]

### WordPiece Tokenization

![[WordPiece Tokenization#^7acc64]]

- [[WordPiece Tokenization]]

### Input Representation

![[bert_input_represntation.png]]



### Pre-Training

#### Task 1: Masked Language Model (MLM)

- [[Self-Supervised Learning]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


#### Task 2: Next Sentence Prediction (NSP)


- [[Next Sentence Prediction as Language Model Training Task]]

### Supervised Fine-Tuning


![[bert.png]]
## Explanation


### Architecture Design of BERT and Its Variants


>[!example]
>The original **English-only** *bidirectional transformer encoder model*, **BERT** (Devlin et al., 2019), consisted of the following:  
>- An *English-only subword vocabulary* consisting of $$30,000$$ *tokens* generated  using the **WordPiece** algorithm (Schuster and Nakajima, 2012). 
>- Hidden layers of *dimensionality* $$d = 768$$  
>- Input **context window** of $$512$$ tokens 
>- $12$ *layers* of transformer blocks, with $12$ (*bidirectional*) *multihead attention*  layers each. 
>- The resulting model has about *$$100 \text{ million}$$ parameters*.
>  
>-- [[devlinBERTPretrainingDeep2019]]  


>[!example]
>The *larger multilingual* **XLM-RoBERTa** model, trained on *$100$ languages*, has  
>- A multilingual subword vocabulary with $$250,000$$ *tokens* generated using the **SentencePiece Unigram LM** algorithm (Kudo and Richardson, 2018b). 
>- $24$ *layers* of transformer blocks, with $16$ *multihead attention* layers each.
>- Hidden layers of size $$d = 1024$$ 
>- Input **context window** of $$512$$ tokens 
>- The resulting model has about *$$550\text{ million}$$ parameters*.
>  
>-- [[liuRoBERTaRobustlyOptimized2019]]  


|                              | **BERT** (**English**)                                                            | **BERT** (**Multilingual**)                                                                                 | **XLM-RoBERTa** (**Multilingual**)                                                                                                  | **DistilBert** (**Multilingual**)                                                                                                                                                                            |
| ---------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Language**                 | English                                                                           | $104$ Language                                                                                              | $100$ Languages                                                                                                                     | $104$ Language                                                                                                                                                                                               |
| **Tokenization**             | **WordPiece** <br>- [[WordPiece Tokenization]]                                    | **WordPiece** <br>- [[WordPiece Tokenization]]                                                              | **SentencePiece Unigram**<br>- [[Unigram Tokenization]] <br>- [[Tokenization of Words and Subwords and SentencePiece Tokenization]] | **WordPiece** <br>- [[WordPiece Tokenization]]                                                                                                                                                               |
| *Vocabulary size*            | $30,000$                                                                          | $110,000$                                                                                                   | $250,000$                                                                                                                           | $110,000$                                                                                                                                                                                                    |
| **Context Window**           | $512$                                                                             | $512$                                                                                                       | $512$                                                                                                                               | $512$                                                                                                                                                                                                        |
| *Layer Depth*                | $12$                                                                              | $12$                                                                                                        | $24$                                                                                                                                | $6$                                                                                                                                                                                                          |
| Mutihead Attention per Layer | $12$                                                                              | $12$                                                                                                        | $16$                                                                                                                                | $12$                                                                                                                                                                                                         |
| *Hidden Layer Dimension*     | $768$                                                                             | $768$                                                                                                       | $1024$                                                                                                                              | $768$                                                                                                                                                                                                        |
| **Parameter size**           | - $110$ million (*base* uncased/cased)<br>- $340$ million (*large* uncased/cased) | - $110$ million (*base* cased)                                                                              | $550$ million                                                                                                                       | $134$ million                                                                                                                                                                                                |
| Model Card                   | [BERT Huggingface](https://huggingface.co/docs/transformers/en/model_doc/bert)    | [BERT multilingual base model Huggingface](https://huggingface.co/google-bert/bert-base-multilingual-cased) | [XLM-RoBERTa Huggingface](https://huggingface.co/docs/transformers/en/model_doc/xlm-roberta)                                        | - [DistilBert Huggingface](https://huggingface.co/docs/transformers/en/model_doc/distilbert)<br>- [distilbert-base-multilingual-cased](https://huggingface.co/distilbert/distilbert-base-multilingual-cased) |



## Dataset in Experiment

### General Language Understanding Evaluation (GLUE) benchmark



### Stanford Question Answering Dataset (SQuAD v1.1 and v2.0)



### Situations with Adversarial Generations (SWAG)






-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]



- [[Bidirectional Recurrent Neural Network]]
- [[Artificial Neural Network and Deep Learning]]

- [[devlinBERTPretrainingDeep2019]]
- [[liuRoBERTaRobustlyOptimized2019]]
- Sanh, V. (2019). DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter. _arXiv preprint arXiv:1910.01108_.


- [[Deep Learning Foundations and Concepts by Bishop]] pp 388 - 390
- [[Speech and Language Processing by Jurafsky]] pp 