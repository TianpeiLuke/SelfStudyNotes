---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/models
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - supervised_fine_tuning_llm
  - instruction_fine_tuning_llm
topics: 
name: Supervised Fine-Tuning or Instruction Fine-Tuning of LLM
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**:  Supervised Fine-Tuning or Instruction Fine-Tuning of LLM

>[!important] Definition
>The **instruction fine-tuning** or **supervised fine-tuning (SFT)** or **instruction/instruct tuning** is a method for making an LLM better at *following instructions*:
>- It involves taking a based pretrained language model and training it to *follow instructions* for *a wide range of tasks*.
>- The resulting model improves its ability to follow instructions generally.

^e2e7b8


- [[Foundational Models for Transfer Learning]]
- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]

## Explanation

>[!info]
>The idea of **instruction fine-tuning** is close to **meta learning.**

- [[Meta Learning]]


>[!quote]
>**Instruction tuning** is a form of supervised learning where the training data consists of *instructions* and we continue training the model on them using the *same  language modeling objective* used to train the original model. 
>- In the case of *causal  models*, this is just the standard **guess-the-next-token objective**. 
>	- The training corpus  of *instructions* is simply treated as *additional training data*, and the gradient-based  updates are generating using *cross-entropy loss* as in the original model training.  
>	- Even though it is trained to predict the next token (which we traditionally think of  as *self-supervised*), we call this method **supervised fine tuning** (or **SFT**) because unlike in pretraining, each instruction or question in the instruction tuning data has  a *supervised objective*: a *correct answer* to the question or a response to the instruction.
>	  
>-- [[Speech and Language Processing by Jurafsky]] pp 249	  

- [[Supervised Learning and Unsupervised Learning]]

### Why SFT?

![[In-Context Learning for LLM#^937794]]

>[!info]
>In order to achieve better performance for **in-context learning**, it is necessary to have **instruction fine-tuning**.

- [[In-Context Learning for LLM]]



## Other Methods of Fine-Tuning

![[instruct_fine_tuning.png]]

>[!quote]
>How does instruction tuning differ from the other kinds of **finetuning** introduced  in Chapter 10 and Chapter 11?  Fig. 12.4 sketches the differences. 
>- In the first example, introduced in, Chapter 10 we can finetune as a way of adapting to a new domain  by just **continuing pretraining** the LLM on data from a new domain. 
>	- In this method  *all the parameters* of the LLM are updated. 
>- In the second example, also from Chapter 10, **parameter-efficient finetuning**,  we adapt to a new domain by *creating some new (small) parameters*, and just adapting them to the new domain. 
>	- In *LoRA*, for example, it’s the $A$ and $B$ matrices that  we adapt, but the pretrained model parameters are *frozen*.  
>- In the **task-based finetuning** of Chapter 11, we adapt to a particular task by  adding a *new specialized classification head* and updating its features via its *own loss function* (e.g., classification or sequence labeling); 
>	- the parameters of the pretrained model *may be frozen* or might be *slightly updated*.  
>- Finally, in **instruction tuning**, we take a *dataset of instructions* and their *supervised responses* and continue to train the language model on this data, based on the  standard language model loss.  
>
>Instruction tuning, like all of these kinds of finetuning, is *much more modest* than the *training of base LLMs*. 
>- Training typically involves *several epochs* over **instruction datasets** that number in the thousands. 
>- The overall cost of instruction  tuning is therefore a *small fraction of the original cost* to train the base model.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 250  

### Continuing Pretraining

- [[Continued Pre-training of Large Language Models]]

### Parameter Efficient Fine-Tuning

- [[Parameter Efficient Fine Tuning or PEFT for Large Language Model]]
	- [[Adapter-Tuning for Large Language Model]]
	- [[Prefix-Tuning for Large Language Model]]
	- [[Prompt-Tuning or Soft-Prompting for Large Language Model]]
	- [[Low Rank Adaptation or LoRA for Large Language Model]]

### Masked Language Model Fine-Tuning

- [[Masked Language Modeling as Language Model Training Task]]
- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Fine-Tuning for Sequence Labeling via BERT]]


## Compare to Preference Alignment

- [[Supervised Fine-Tuning and Preference Alignment for LLM]]
- [[Preference Alignment for LLM]]

- [[Reinforcement Learning with Human Feedbacks or RLHF for LLM]]
- [[Direct Preference Optimization for Alignment in LLM]]






-----------
##  Recommended Notes and References



- [[Large Language Model and Pretrained Language Models]]



- [[Transfer Learning]]
- [[Speech and Language Processing by Jurafsky]] pp 214. 249 - 254