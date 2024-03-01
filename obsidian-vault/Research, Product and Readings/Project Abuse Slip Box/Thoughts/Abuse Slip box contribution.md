---
tags:
  - project
  - abuse_slip_box
aliases: 
date of note: 2024-02-22
---
>[!info] 
>One of the main challenges of the current buyer abuse prevention system

- [[Issues of BAP data management system]]

## Proposal

We propose the **Abuse Slip Box** which is a _graph-based knowledge management system_. Each node of the graph is a **note**containing an atomic piece of information in the process of investigation (e.g. CS contact for a given order, the annotation from ARI at given refund task). The text in these nodes follows the same unified format based on the result of text summarization, topic categorization as well as keyword extraction. Notes are connected via their context similarity as well as their association with the same order/customer/workflow in the order-concession life cycle.


## Contributions

>[!contribution] 
>What is the contribution of the proposed abuse slip box?
 
The contributions are listed below:  

1. Abuse Slip Box enhances LLM with domain expertise based on an efficient information retrieval system from various interconnected notes. The LLM in-context learning using Abuse Slip Box would be used in automated abuse categorization and action suggestions. It would also fill in the gap in reasoning behind the investigation process.   
    
2. Abuse Slip Box sets up standards for notes that summarize customer contacts from different channels including BSM, CSC, seller/ARI referral, etc. Besides, ARI annotations, paragraphs in SOP documents, rule descriptions etc are also collected and summarized into same format of notes. This greatly simplifies the digestion of information from heterogenous sources.   
    
3. Abuse Slip Box provides a single knowledge management service to store and organize both input and output data from online evaluation workflows. This allows the people in ML, ARI and product team to combine, review and analyze all relevant information along the order-concession life circle simply by traversing the path in the network.   
    
4. Abuse Slip Box helps scientists to detect clusters and anomalies through graph mining. Its network structure naturally reveals abuse patterns that would share across multiple accounts, or from multiple workflows. This technique has already been used in many graph-based MO detect system such as Tattletale. Abuse Slip Box can be viewed as an upgrade from current existing graph-based system to incorporate more context information.   
    
5. Abuse Slip can also spot inconsistency in ARI decisions by connecting ARI decisions, customer contacts with SOPs.









-----------
##  Recommended Notes