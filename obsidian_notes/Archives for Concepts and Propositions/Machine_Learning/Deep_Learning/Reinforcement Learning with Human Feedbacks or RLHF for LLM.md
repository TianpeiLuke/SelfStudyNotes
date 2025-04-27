---
tags:
  - concept
  - deep_learning/models
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - reinforcement_learning_with_human_feedbacks
  - rlhf_llm
  - rlhf
  - RLHF
keywords:
  - reinforcement_learning_with_human_feedbacks
  - rlhf_llm
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
name: Reinforcement Learning with Human Feedbacks or RLHF for LLM
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Reinforcement Learning with Human Feedbacks or RLHF for LLM

>[!important] Definition
>**Reinforcement Learning with Human Feedback (RLHF)** is a framework for training models, particularly large language models, by combining *human preferences* with *reinforcement learning* techniques. 

- [[Supervised Fine-Tuning and Preference Alignment for LLM]]

![[reinforcement_learning_human_feedback.png]]

### Basic Procedure

>[!important]
>Instead of relying solely on predefined reward functions, **RLHF** 
>- first *collects human feedback*—typically in the form of preference rankings between model outputs—
>- and uses this feedback to *train a reward model* that approximates human judgment. 
>- The main model is then *fine-tuned* using reinforcement learning 
>	- (often Proximal Policy Optimization, PPO) to maximize the learned reward signal, 
>	- aligning the model's behavior more closely with *human values*, intentions, or quality expectations. 


### RLHF Algorithms

- [[Proximal Policy Optimization or PPO Algorithm]]
- [[Generalized Advantage Estimation or GAE in PPO]]
- [[Group Relative Policy Optimization or GRPO Algorithm]]


## Explanation

>[!info]
>RLHF enables powerful models to *generalize better* to nuanced tasks where explicit supervision is difficult to define, and it has been foundational in the development of aligned AI systems like ChatGPT.


>[!quote]
>In this paper, we *combine* the **pretraining** advances in natural language processing with **human preference learning**. 
>- We *fine-tune pretrained language models* with *reinforcement learning* rather than supervised learning, using a **reward model** trained from human preferences on text continuations.
>
>...
>Our motivation is NLP tasks where *supervised data sets* are *unavailable* or *insufficient*, and where *programmatic reward functions* are *poor* proxies for our true goals.  
>  
>-- [[zieglerFineTuningLanguageModels2020a]]   







-----------
##  Recommended Notes and References


- [[Direct Preference Optimization for Alignment in LLM]]
- [[zieglerFineTuningLanguageModels2020a]] Ziegler, D. M., Stiennon, N., Wu, J., Brown, T. B., Radford, A., Amodei, D., ... & Irving, G. (2019). Fine-tuning language models from human preferences. _arXiv preprint arXiv:1909.08593_.

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Large Language Model and Pretrained Language Models]]
- [[Foundational Models for Transfer Learning]]


- [[Valued-based and Policy-based Reinforcement Learning]]
- [[Markov Decision Process]]