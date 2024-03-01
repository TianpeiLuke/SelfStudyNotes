---
tags:
  - project
  - abuse_slip_box
  - planning
aliases: 
date of note: 2024-02-29
---
## Goal  

- development of **graph-based RAG using LLM**. 

## Task

- Develop a sample selection mechanism that drop irrelevant text; 
- Create a real-time data ingestion and processing pipeline that provides continual input to the graph-based storage
- Develop regular review mechanism that 
	- delete or summarize notes after some time (retention policy), except for SOP
	- summarizes similar notes into one and merge node in graph
	- traverse through paths in graph to spot inconsistency; correct labels or connections if inconsistency exists
	- allow human-in-the-loop for review, audit and deep dive
- Develop graph neural network to detect graph clusters and to propagate/reverse labels 
- Create a Deep Dive Dashboard to summarize and describe abuse events related to given query

## Timeline

TBD

## Milestones 

- A progressive summarization mechanism that build a hierarchical mult-layer graph database
- A regular review process that 
	- pruning edges, merging or deleting notes that no longer relevant
	- re-build indexing system / re-rank notes
	- re-evaluate following updates of notes in the workflow path
- Graph clustering method that spot cluster of notes in Abuse Slip Box, summarize it into paragraph and narrative
- A Deep Dive Dashboard that provides summary and description of abuse events related to given query


## Progress Schedule





---

## Resources




-----------
##  Recommended Notes