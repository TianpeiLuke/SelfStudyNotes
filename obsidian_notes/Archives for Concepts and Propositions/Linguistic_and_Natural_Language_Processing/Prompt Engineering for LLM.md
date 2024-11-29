---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - prompt_engineering
topics:
  - natural_language_processing/large_language_models
name: Prompt Engineering for LLM
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Prompt Engineering for LLM

>[!important] Definition
>A **prompt** is a piece of text or a set of *instructions* that you provide to a *Large Language Model (LLM)* to trigger a specific response or action.

^0e4cf4

- [[In-Context Learning for LLM]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Parameter Efficient Fine Tuning or PEFT for Large Language Model]]

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


-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Large Language Model and Pretrained Language Models]]
- [[Foundational Models for Transfer Learning]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 394
- [[Speech and Language Processing by Jurafsky]] pp 243
- Liu, P., Yuan, W., Fu, J., Jiang, Z., Hayashi, H., & Neubig, G. (2023). Pre-train, prompt, and predict: A systematic survey of prompting methods in natural language processing. _ACM Computing Surveys_, _55_(9), 1-35. [[liuPretrainPromptPredict2023]]
- Medium
	- [LLM Prompt Engineering for Beginners: What It Is and How to Get Started](https://medium.com/thedeephub/llm-prompt-engineering-for-beginners-what-it-is-and-how-to-get-started-0c1b483d5d4f)