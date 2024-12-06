---
tags:
  - concept
  - natural_language_processing/question_answering
  - natural_language_processing/chatbot
  - natural_language_processing/information_extraction
keywords:
  - question_answering_problem
topics:
  - natural_language_processing/question_answering
name: Question Answering Problem
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Question Answering Problem

>[!quote]
>Describing precisely what we are talking about when we refer to **Question Answering (QA)** is probably not as easy as it could be expected. 
>- From a very general perspective QA can be defined as an *automatic process* capable of **understanding questions** formulated in a *natural language* such as English and **responding** exactly with the *requested information*. 
>  
>However, this apparently simple definition turns very complex when we analyze in detail which are the characteristics and functionality an **“*ideal*” QA system** should have. 
>- This system should be able to 
>	- *determine the information need* expressed in a question, 
>	- *locate* the required information, 
>	- extract it, 
>	- and then *generate an answer* 
>	- and *present* it according to the requirements expressed in the question. 
>- Moreover, this ideal system should be able to *interpret questions* and *process documents* that are written in *unrestricted-domain natural languages*, which would allow for a *comfortable and appropriate interaction* by users. 
>  
>-- [[Handbook of Natural Language Processing by Indurkhya]] pp 485  

>[!important] Definition
>An **open-domain question answering** is where the system 
>- deals with questions posed in *natural language*, and 
>- *answers* are extracted from a very large document collection


>[!important] Definition
>Question answering systems are designed to fill **human information needs**.

>[!important] Definition
>Question answering systems often focus on a useful subset of information needs:  
>- **factoid questions**, questions of *fact* or *reasoning* that can be answered with simple  facts expressed in short or medium-length texts


### Question Answering System

![[question_answering_system.png]]

#### Question Analysis


#### Document / Passage Selection


#### Answer Extraction



## Explanation

>[!info]
>Since a lot of information is present in *text form* (on the web or in other data like  our email, or books), *question answering* is closely related to the **information retrieval** task behind **search  engines**.

- [[Information Retrieval]]


## LLM for Question Answering

- [[Retrieval Augmented Generation]]


-----------
##  Recommended Notes and References

- [[Information Retrieval with Encoder Language Models]]


- [[Speech and Language Processing by Jurafsky]] pp 289
- [[Handbook of Natural Language Processing by Indurkhya]] pp 485 - 511
- [[Practical Natural Language Processing by Vajjala]] pp 200 - 201
- [[Artificial Intelligence Modern Approach by Russell]] pp 872