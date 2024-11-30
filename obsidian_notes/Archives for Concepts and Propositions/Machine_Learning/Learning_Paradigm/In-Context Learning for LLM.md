---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - in_context_learning
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
name: In-Context Learning for LLM
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: In-Context Learning for LLM

![[Prompt Engineering for LLM#^0e4cf4]]

>[!important] Definition
>**In-context learning (ICL)** is a paradigm that allows language models to learn tasks given only a few *example*s in the form of demonstration.
>
>Let $x_{k}$ be input text, and $y_{k}\in \mathcal{Y}$ be  a set of *candidate answers* for $k=1\,{,}\ldots{,}\,m$. 
>
>Define the **demonstration** $C$ as a set of examples $$C:= \{ I, s(x_{1}, y_{1})\,{,}\ldots{,}\,s(x_{m}, y_{m}) \},\text{ or }\; C:= \{s'(x_{1}, y_{1},I)\,{,}\ldots{,}\,s'(x_{m}, y_{m},I) \}$$ where 
>- $I$ is the *instruction* or **prompt** for the task, and
>- $$s'(x_{k}, y_{k}, I)$$ is an example written in natural language accorrding to the task.
>  
>The **in-context learning** on new text $x$ refers to the case when a pretrained language model $p$  takes the *candidate answer* with *maximum score* as the *prediction* of response to $x$. That is,
>$$
>\hat{y} = \arg\max_{k=1\,{,}\ldots{,}\,m}\;p(y_{k}\,|\,x,\, C)
>$$  

- [[Few-Shot Learning and Zero-Shot Learning]]
- [[Prompt Engineering for LLM]]
- [[Generative Pre-trained Transformer or GPT]]

>[!quote]
>**Prompts** get language models to generate text, but they also can be viewed as  a **learning signal**, because these demonstrations can help language models learn  to perform novel tasks.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 242




## Explanation

>[!quote]
>Now, as of this writing in 2021, we are in the middle of a second sea change, in which the “**pretrain, fine-tune**” procedure is replaced by one in which we dub “**pre-train, prompt, and predict**.” 
>- In this paradigm, instead of *adapting pre-trained LMs* to downstream tasks via *objective engineering*, downstream tasks are reformulated to look more like those solved during the original LM training with the help of a textual **prompt**. ...
>- In this way, by *selecting the appropriate prompts* we can manipulate the model behavior so that the pre-trained LM itself can be used to **predict** the desired output, sometimes even *without any additional task-specific training*. 
>- The **advantage** of this method is that, given a suite of appropriate prompts, a single LM trained in an entirely unsupervised fashion can be used to solve a great number of tasks. 
>- However, as with most conceptually enticing prospects, there is a catchthis method introduces the necessity for **prompt engineering**, finding the most appropriate prompt to allow a LM to solve the task at hand.
>  
>-- [[liuPretrainPromptPredict2023]]   

- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]

>[!quote]
>According to the definition, we can see that **ICL** differs from related concepts as follows: 
>- (1) **Prompt Learning**: prompts can be *discrete templates* or *soft parameters* that encourage the model to predict the desired output. ICL can be regarded as a *subclass* of **prompt tuning** where the demonstration examples are part of the prompt. Liu et al. (2023c) made a thorough survey on prompt learning, but ICL was not included in their study. 
>- (2) **Few-shot Learning**: few-shot learning is a general machine learning approach that involves adapting model parameters to perform a task with a limited number of supervised examples (Wang and Yao, 2019). In contrast, ICL does *not require parameter updates* and is directly performed on pretrained LLMs.
>
>-- [[dongSurveyIncontextLearning2024]] 

- [[Prompt-Tuning or Soft-Prompting for Large Language Model]]
- [[Transfer Learning]]

### Limitation of In-Context Learning Model Alignment

>[!quote]
>LLMs as we’ve described them so far turn out to be *bad at following instructions*. 
>- Pretraining isn’t sufficient to make them **helpful**. 
>	- We’ll introduce **instruction tuning**, a technique that helps LLMs learn to *correctly respond* to instructions by *finetuning* them on a corpus of *instructions* with their corresponding response.  
>- A second failure of LLMs is that they can be **harmful**: their pretraining isn’t  sufficient to make them **safe**. 
>	- Readers who know Arthur C. Clarke’s 2001: A Space  Odyssey or the Stanley Kubrick film know that the quote above comes in the context  that the artificial intelligence Hal becomes paranoid and tries to kill the crew of the  spaceship. Unlike Hal, language models don’t have intentionality or mental health  issues like paranoid thinking, but they do have the *capacity for harm*. 
>	- Pretrained language models can say things that are *dangerous or false* (like giving unsafe medical  advice) and they can verbally attack users or say *toxic or hateful* things.
>	  
>-- [[Speech and Language Processing by Jurafsky]]	  

^937794

- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Preference Alignment for LLM]]



## Applications

### Prompt Engineering

- [[Prompt Engineering for LLM]]

### Chain-of-Thought Reasoning

- [[Chain-of-Thought Prompting]]

### ReAct

- [[ReAct as LLM Agent for Reasoning and Acting]]




-----------
##  Recommended Notes and References



- [[Large Language Model and Pretrained Language Models]]
- [[Foundational Models for Transfer Learning]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 394
- [[Speech and Language Processing by Jurafsky]] pp 247
- Dong, Q., Li, L., Dai, D., Zheng, C., Ma, J., Li, R., ... & Sui, Z. (2022). A survey on in-context learning. _arXiv preprint arXiv:2301.00234_. [[dongSurveyIncontextLearning2024]] 