---
tags:
  - project
  - abuse_slip_box
  - planning
aliases: 
date of note: 2024-02-29
---
## Goal  

- development of **automated summarization workflow** for various of docs

## Task

- Combining with text digestion workflow for CS, BSM, PR, ARI, and develop corresponding parsing, preprocessing workflow. 
- Then use pre-trained language model to summarize text from CSC, BSM, PR, ARI into a short note
- Build topic models that summarize the topic or classify the topic
- Use encoder language model to output embedding based on summary, topic and keywords etc.
- We could limit our scope to cover only a few concession abuse types (DNR/NOTR, MDR).

## Timeline

2024 Q2


## Milestones 

- Define unified format of notes for CSC, BSM, PR, ARI annotations
- Prompts for LLM based summarization; 
- Experimentation on summarization with LLM supported by BedRock (e.g. CloudeV2 )
- Develop a prototype pipeline that takes in the raw text, and output formatted notes based on summarization and topic modeling


## Progress Schedule





---

## Resources

- BSM data sources (existing MDS source)
- CSC data sources (AIT, or Patronus)
- ARI annotations (FAP table, Post-investigation Workflow)
- Tabular features for abuse classification such as SI, order/concession histories, tracking info, (MDS, OTF, Collaborate with Zora to get Screenshot from Paragon)
- SOP documents
- Code for BSM preprocessing
- Code for CSC preprocessing


-----------
##  Recommended Notes