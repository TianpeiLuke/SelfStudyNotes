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

- [[Positional Embeddings of Large Language Models]]

### Pre-Training

#### Task 1: Masked Language Model (MLM)

![[Masked Language Modeling as Language Model Training Task#^0229dc]]

- [[Masked Language Modeling as Language Model Training Task]]
- [[Self-Supervised Learning]]
- [[Sequence Labeling Task]]

![[Masked Language Modeling as Language Model Training Task#^7164fd]]

>[!important]
>In training BERT, only **15%** of training samples are used to learn weights.

![[masked_language_model_training.png]]

#### Task 2: Next Sentence Prediction (NSP)

![[Next Sentence Prediction as Language Model Training Task#^48fb58]]

![[Next Sentence Prediction as Language Model Training Task#^3c0dea]]

![[Next Sentence Prediction as Language Model Training Task#^c626ba]]

- [[Next Sentence Prediction as Language Model Training Task]]
- [[Sequence Classification and Sequence-Pair Classification]]

![[next_sentence_prediction_loss.png]]

### Supervised Fine-Tuning

- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Fine-Tuning for Sequence Labeling via BERT]]

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

- [[ColBERT as Multi-Representation Bi-Encoder Structure for Dense Information Retrieval]]

### Monolingual vs. Multilingual

>[!quote] 
>For many purposes, a **pretrained multilingual model** is *more practical* than a monolingual model, since it avoids the need to build many (a hundred!) separate monolingual models. And multilingual models can improve performance on low-resourced languages by leveraging linguistic information from a *similar language* in the training data that happens to have more resources. 
>
>- Nonetheless, when the *number of languages grows very large*, multilingual models exhibit what has been called the **curse of multilinguality** (Conneau et al., 2020): 
>	- the performance on *each* language *degrades* compared to a model training on *fewer languages*. 
>
>- Another problem with multilingual models is that they ‘**have an accent**’: 
>	- *grammatical structures* in higher-resource languages (often English) *bleed* into lower-resource languages; 
>	- the vast amount of English language in training makes the model’s representations for low-resource languages slightly more *English-like* (Papadimitriou et al., 2023).
>
>-- [[Speech and Language Processing by Jurafsky]] pp 230


## Dataset in Experiment

### General Language Understanding Evaluation (GLUE) benchmark



### Stanford Question Answering Dataset (SQuAD v1.1 and v2.0)



### Situations with Adversarial Generations (SWAG)


## Variants

- [[devlinBERTPretrainingDeep2019]]
- [[liuRoBERTaRobustlyOptimized2019]]
- [[warnerSmarterBetterFaster2024]]
- [[Dense Text Retrieval with Pretrained Language Models]]
- [[ColBERT as Multi-Representation Bi-Encoder Structure for Dense Information Retrieval]]
- [[Sentence-BERT for Sentence Embedding]]




-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]



- [[Bidirectional Recurrent Neural Network]]
- [[Artificial Neural Network and Deep Learning]]


- Sanh, V. (2019). DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter. _arXiv preprint arXiv:1910.01108_.


- [[Deep Learning Foundations and Concepts by Bishop]] pp 388 - 390
- [[Speech and Language Processing by Jurafsky]] pp 