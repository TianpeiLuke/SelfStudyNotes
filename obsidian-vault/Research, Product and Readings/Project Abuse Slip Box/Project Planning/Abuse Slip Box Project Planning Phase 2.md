---
tags:
  - project
  - abuse_slip_box
  - planning
aliases: 
date of note: 2024-02-29
---
## Goal  

- development of **graph-based knowledge management system**. 

## Task

- For each note, create a list that point to notes that belong to the same customerID, orderID, or workflow; 
- For each note, create a list that includes all notes with same topics. 
- For text summary, generate embeddings via encoder pre-trained language model
- Develop vector-database solution based on AWS OpenSearch or other open source system
- For each note, retrieve top 5 notes according to approximate nearest neighbor search. Could use the topic-based adjacency list to confine the search space.
- Could use other models and techniques for link prediction.

## Timeline

TBD


## Milestones 

- Three Adjacency lists:
	- customer/order/workflow adjacency list
	- context adjacency list
	- topic adjacency list
	  
- Vector database for embeddings of notes


## Progress Schedule





---

## Resources

- DeepCare infrastructure
- Tattletale infrastructure (? need to check)
- OpenSearch database (need to check)
- Pre-trained Encoder models such as BERT, ROBERTa, or LLM such as Titan Embedding model


-----------
##  Recommended Notes