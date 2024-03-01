---
tags:
  - project
  - context_enhanced_bap
  - customer_service_contact
  - data_access
aliases:
  - 0801csmodetection00
date of note: 2024-02-27
name: CS Chat MO detection
author: Travis Li
email: wxl@amazon.com
---


## Summary

This project aims at identifying buyers who adopt a playbook in order to get refund from CS agents. The playbooks contain a set of instructions on how to communicate with CS agents and what questions are expected and what answers should be used. Such playbook hidden the true intent of buyer’s refund requests, allowing abusive buyer to get refund by taking advantages of the loopholes in pre-existing SOPs. ML scientist used NLP technique to spot the similarities behind two CS contact transcripts. By associating similar contacts into one cluster, we greatly improve the recall of detection while maintaining the efficiency of searching algorithm. Experiment results show that the model using CS contacts input can achieve 57% customer closure rate after retrieval and investigation, a 264% increase as compare to current closure rate of 21.6%.
### Owner

Data Scientist II, Travis Li, wxl@amazon.com
Applied Science Manager, Brandon Quach, qcq@amazon.com
Senior SDM, Venkatesha, Vishwas Koppa vishwasv@amazon.com

## CSMO Offline detection

![[CSMO Offline detection .png]]

Steps in offline Chat MO detection involve:
> [!quote]
> 1. First we **learn the chat embedding** using a fine-tuned sentence-BERT model with triplet-loss.
> 2. Second, we calculated pair-wise cosine similarity as linkage to construct a graph and **detect clusters of similar chats**.
> 3. Third, we did **cluster ranking** by designing a heuristic linear model that ensembles lexical similarity with other three model scores: 1) an XGBoost model for known abuse prediction, 2) a negative sentiment score using a DistilBERT model and 3) a part-of-speech (POS) mixture model to address exaggerative language often used by abusers.


>[!Limitations]
>The offline pipeline works well but it fails to  
> - react quickly in terms of enforcement on bad actors or identifying new abusive patterns. **Around 50% of the accounts are closed already due to our reports are usually around 2 weeks’ delay.** Another example is the low dollar UK DNR, we found it spread to US/DE through chat report.
> 
> - share signals/variables to benefit other systems due to the model is running offline.


## CSMO Online detection - A unified synchronous system

![[CSMO Online detection - A unified synchronous system.png]]


>[!quote]
>While our offline system is more about accumulating past week’s CS chats and building community in order to find common patterns, our online system is more about accumulation in real-time to form a “catalogue”, and through KNN search with cut-off distance to filter out “comparison pool” that will help to take downstream actions: auto-enforcement/sideline/accumulation, etc.  
>
> **We propose to trigger CSMO evaluation for each incoming CS contact from a concession, the CS signals(OTF) and CSMO inference are calculated.** The first **language model module** **(step 1)** will transform the CS text data into embedding or signals that can be used downstream. The **CSMO inference workflow (step 4,5,6,7,8,9)** is trying to retrieve related CS data from the CS catalogue (embedding store) and make decisions (sideline/accumulation) based on the retrieval results; **The Chat OTF calculator** **(step 2,3)** will work on creating CS-related OTFs that can benefits other downstream tasks (like writing rules, etc.)


## Result

### Offline Solution

- a total of 364 accounts closed from 644 queued accounts (57% closure rate, comparing to the average Tattletale rule closure rate 21.6%) from 24 new MOs with 4 sidelined batches of english CS chat messages.


### Online Solution Sample Queueing

>[!Example]
> Queuing Logic:
> - queueing to human investigator for review based on *higher community average similarity score*, *sentiment score (negative sentence rate)*  and *POS tagging score (ADV and ADJ rate)* 
>   
> Result:
> - one pattern may lead to an abuse with estimated 231K USD




## Which stage to deploy

We are looking for deployment in Refund Interception (RI) and Pre-Fulfillment Workflow (PFW)  



---
## Quip link: 

- proposal and offline solution: [quip](https://quip-amazon.com/9IYKAX8r8AtE/RASP-detection-through-chat-Phase-1)
- online solution [quip](https://quip-amazon.com/tBsmAyELo083/CSMO-online-solution)