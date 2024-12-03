---
tags:
  - concept
  - machine_learning/models
  - natural_language_processing/information_extraction
  - information_retrieval/information_extraction
keywords:
  - information_extraction
topics:
  - natural_language_processing/information_extraction
name: Information Extraction
date of note: 2024-09-04
---

## Concept Definition

>[!important]
>**Name**: Information Extraction

>[!important] Definition
>**Information Extraction (IE)** is a term that’s used to refer to a range of different tasks of varying complexity. 
>- The overarching *goal* of IE is to extract “*knowledge*” from text, and each of these tasks provides different information to do that.
>

>[!quote]
>**Information extraction (IE)** is the process of scanning text for information *relevant to some interest*, including extracting *entities*, *relations*, and, most challenging, *events*—or who did what to whom, when, and where. 
>- It requires *deeper analysis* than **keyword searches**, but its aims *fall short* of the very hard and *long-term problem* of **text understanding**, where we seek to capture all the information in a text, along with the speaker’s or writer’s intention. 
>
>- IE represents a *midpoint* on this spectrum, where the aim is to capture structured information without sacrificing *feasibility*. 
>- IE typically focuses on **surface linguistic phenomena** that do not require deep inference, and it focuses on the phenomena that are *most frequent* in texts.
>  
>-- [[Handbook of Natural Language Processing by Indurkhya]] pp 511  


>[!important] Definition
>**Information Extraction (IE)** includes the following tasks:
>- **Keyword Extraction** or **Keyphrase Extraction (KPE)**: refers to the tasks that identify keywords and key phrases that related to knowledge of interest.
>- **Name Entity Recognition (NER)**: refers to the tasks that identify the name, organization, location, time, geo-location, etc.
>- **Name Entity Disambiguation and Linking**: refers to the tasks that differentiate different name entities with same name
>- **Relation Extraction**: refers to the tasks that extract the relationship between name entities.

- [[Keyphrase Extraction]]
- [[Regular Expression Advanced Operations]]
- [[Regular Expression Pattern Basics]]
- [[Name Entity Recognition]]
- [[Name Entity Disambiguation and Linking]]
- [[Relation Extraction]]
- [[Event Extraction]]

![[information_extraction_pipeline.png]]


## Explanation


## LLM in Information Extraction

![[llm_ie_survey.png]]

![[ie_backbone_llm_survey_2024_part1.png]]
![[ie_backbone_llm_survey_2024_part2.png]]



- [[Large Language Model and Pretrained Language Models]]
- Xu, D., Chen, W., Peng, W., Zhang, C., Xu, T., Zhao, X., ... & Chen, E. (2024). Large language models for generative information extraction: A survey. _Frontiers of Computer Science_, _18_(6), 186357.

## Common Datasets and Benchmarks

![[ie_benchmark_survey_2024_part1.png]]
![[ie_benchmark_survey_2024_part2.png]]


>[!example]
>**CoNLL03**.
>- Sang E F T K, De Meulder F. Introduction to the CoNLL-2003 shared task:  language-independent  named  entity  recognition.  In:  *Proceedings of the 7th Conference on Natural Language Learning*. 2003, 142−147
>   
>The **CoNLL03** is a representative dataset for *NER*,  including 
>- 1,393  news articles in English  
>- and 909  news articles in German. 
>- The English portion of the corpus was sourced from the *Shared Task dataset* curated by Reuters. 
>- This dataset encompasses annotations for **four distinct entity types**: 
>	- PER  (person),  
>	- LOC  (location),  
>	- ORG  (organization),  
>	- and MISC (including all other types of entities).
>
>

>[!example]
>**CoNLL04.**  
>- Roth  D,  Yih  W  T.  A  linear  programming  formulation  for  global inference  in  natural  language  tasks.  In:  *Proceedings  of  the  8th Conference on Computational Natural Language Learning*. 2004, 1−8
>
>The **CoNLL04** is a well-known benchmark dataset for *RE* tasks, comprising  
>- sentences extracted from news articles that each contain at least *one entity-relation triple*.  
>- It  has 
>	- **four kinds of entities**  (PER,  ORG,  LOC,  OTH) 
>	- and **five kinds of relations** (Kill, Work For, Live In, OrgBased In, Located In).

>[!example]
>**ACE05.**  
>- Walker  C,  Strassel  S,  Medero  J,  Maeda  K.  Ace  2005  multilingual training  corpus-linguistic  data  consortium.  See catalog.ldc.upenn.edu/LDC2006T06 website, 2005
>
>**Automatic Content Extraction 05**  is widely recognized and utilized for IE tasks. 
>- It serves as a valuable resource to assess the efficacy of automated systems in extracting structured information from diverse textual sources, encompassing news  articles, interviews, reports, etc. 
>- Moreover, this dataset covers a broad range of genres including politics,  economics,  sports,  among  others. 
>- Specifically for the EE task within ACE05, it comprises 
>	- 599 news documents that encapsulate  33  *distinct event types*  and 22 *argument roles*.




-----------
##  Recommended Notes and References

- [[Information Retrieval]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 953 - 960
- [[Speech and Language Processing by Jurafsky]] pp 435
- [[Handbook of Natural Language Processing by Indurkhya]] pp 511
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 112, 131, 376
- [[Practical Natural Language Processing by Vajjala]] pp 164
- [[Artificial Intelligence Modern Approach by Russell]] pp 873 - 876