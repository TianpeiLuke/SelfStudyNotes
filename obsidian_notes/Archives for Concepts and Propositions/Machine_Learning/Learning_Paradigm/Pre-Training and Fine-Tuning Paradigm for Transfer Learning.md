---
tags:
  - concept
  - machine_learning/strategy
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
keywords:
  - pre_training_ml
  - fine_tuning_ml
topics:
  - machine_learning_strategy
name: Pre-Training and Fine-Tuning Paradigm for Transfer Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Pre-Training and Fine-Tuning Paradigm for Transfer Learning

>[!important] Definition
>**Pre-training** refers to training a machine learning model on a *large, general-purpose dataset* for a *related but broader task*. 
>- The goal is to initialize the model with knowledge that can later be *adapted* to a *specific task*.
>- With pre-training, the training  for the new task does *not start from scratch*. 
>- This allows us to leverage the patterns learned from the large dataset, and improve the performance on specific task with *fewer computation* and *less data.*

^7e9176

>[!important] Definition
>**Fine-tuning** involves taking a *pre-trained model* and *further training* it on a *smaller, task-specific dataset*. 
>- The goal is to *adapt the general knowledge* from pre-training to solve a more focused, *domain-specific problem*.
>- The purpose is to *refine* the model's weights so that it performs well on the *new task* while *leveraging the knowledge* gained during pre-training.

^036480



>[!quote]
>- When data for task $A$ is very **scarce**, we might simply **re-train** the *final layer* of the network. 
>- In contrast, if there are more data points, it is feasible to *retrain several layers*. 
>- The process of learning parameters using *one task* that are then applied to *one or more other tasks* is called **pre-training**. 
>	- Note that for the new task, instead of applying stochastic gradient descent to the whole network, it is much more efficient to send the new training data *once* through the *fixed pre-trained network* so as to evaluate the training inputs in the new representation. 
>	- Iterative gradient-based optimization can then be applied just to the *smaller network* consisting of the *final layers*. 
>- As well as using a pre-trained network as a fixed pre-processor for a different task, it is also possible to apply **fine-tuning** in which the whole network is adapted to the data for task $A$. 
>	- This is generally done with a very *small learning rate* for a *limited number of iterations* to ensure that the network does not over-fit to the relatively small data set available for the new task.
>	  
>-- [[Speech and Language Processing by Jurafsky]] pp 189 - 190	  



![[pretrain_finetuning_llm.png]]

### Transfer Learning

![[Transfer Learning#^3eb9a1]]

>[!important] Definition
>The **pre-train and fine-tune** approach can be seen as learning an optimal function $f^{t}\in \mathcal{H}^{t}$ via *proximal regularized optimization* on *target distribution* $\mathcal{D}^{t}$
>$$
>f^{t} := \arg\min_{f\in \mathcal{H}^{t}}\;\mathbb{E}_{ (x_{m},y_{m}) \sim \mathcal{D}^{t} }\left[  \ell(y_{m}, f(x_{m})) \right] + \lambda \;\lVert f - f^{s} \rVert_{\mathcal{H}^{t}} 
>$$
>where $f^{s}$ is the *empirical risk minimizer* on *source distribution* $$f^{s} = \arg\min_{f\in \mathcal{H}^{s}}\;\mathbb{E}_{ (x_{n},y_{n}) \sim \mathcal{D}^{s} }\left[  \ell(y_{n}, f(x_{n})) \right] $$


- [[Transfer Learning]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Proximal Algorithm]]
- [[Regularized Loss Minimization]]

## Explanation

>[!info]
>The **pretraining-finetuning** is a general mechanism for *transfer learning* which adapts general knowledge to specific domain.

>[!quote]
>**Fully supervised learning**, where a *task-specific model* is trained solely on a *dataset* of input–output examples for the target task, has long played a central role in many machine learning tasks, and natural language processing (NLP) was no exception. 
>- Because such *manually annotated* datasets are *ever-insufficient* for learning high-quality models, early NLP models relied heavily on **feature engineering**, where NLP researchers or engineers used their *domain knowledge* to define and extract *salient features* from raw data and provide models with the appropriate inductive bias to learn from this limited data....
>
>However, from 2017 to 2019 there was a sea change in the learning of NLP models, and this fully supervised paradigm is now playing an ever-shrinking role. Specifically, the standard shifted to the **pre-train and fine-tune paradigm**.
>-  In this paradigm, a model with a fixed architecture is **pre-trained** as a **language model (LM)**, predicting the probability of observed textual data. 
>- Because the *raw textual data* necessary to train LMs is available in abundance, these LMs can be trained on *large datasets*, in the process learning *robust general-purpose features* of the language it is modeling. 
>- The above *pre-trained LM* will be then *adapted* to *different downstream tasks* by introducing additional parameters and **fine-tuning** them using task-specific objective functions. 
>- Within this paradigm, the focus turned mainly to **objective engineering**, designing the training objectives used at both the pre-training and fine-tuning stages.
>  
>  
>-- Liu, P., Yuan, W., Fu, J., Jiang, Z., Hayashi, H., & Neubig, G. (2023). Pre-train, prompt, and predict: A systematic survey of prompting methods in natural language processing. _ACM Computing Surveys_, _55_(9), 1-35. [[liuPretrainPromptPredict2023]]  



## Examples


### Convoluational Neural Network

- [[Convolutional Filters]]
- [[Convolutional Neural Network]]


### Representation Learning

- [[Representation Learning]]
- [[Word Embedding]]

### Large Language Models

- [[Foundational Models for Transfer Learning]]
- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Large Language Model and Pretrained Language Models]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Fine-Tuning for Sequence Labeling via BERT]]


-----------
##  Recommended Notes and References


- [[Deep Learning Foundations and Concepts by Bishop]] pp 189
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 739
- [[Deep Learning by Goodfellow]] pp 314, 519
- [[Speech and Language Processing by Jurafsky]] pp 145, 203
- [[Foundations of Computer Vision by Torralba]] pp 545 - 546

- Liu, P., Yuan, W., Fu, J., Jiang, Z., Hayashi, H., & Neubig, G. (2023). Pre-train, prompt, and predict: A systematic survey of prompting methods in natural language processing. _ACM Computing Surveys_, _55_(9), 1-35. [[liuPretrainPromptPredict2023]]