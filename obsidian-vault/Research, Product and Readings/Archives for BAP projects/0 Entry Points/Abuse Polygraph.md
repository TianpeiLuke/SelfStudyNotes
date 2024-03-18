---
tags:
  - project
  - context_enhanced_bap
  - customer_service_contact
aliases:
  - 0801csabusepolygraph00
date of note: 2024-02-27
name: CS Abuse Polygraph
author:
  - Cheng Ji
email: cjiamzn@amazon.com
---

## Summary

The Abuse Polygraph model is an NLP based deception detection model which utilizes customer contact transcript to detect customer lying about their experience when requesting any type of concessions from Amazon. The BERT based offline prototype model we built on ARI labels achieves 0.84 AUC on the currently undetected population (population that was not routed to CAP by the current production model), which translates to an incremental saving of $350K per week if we take actions on the top 5% of the accounts. We have also conducted offline audit with CAP and ARI agents, which shows out of riskiest 500 contacts according to the model, CAP agents find 55% of them are abusive, and for accounts that’s also queued to ARI by other existing mechanisms, 61 out of 68 (90%) accounts were actioned later.

## Owner

Senior Applied Scientist, Cheng Ji, cjiamzn@amazon.com
Senior Applied Scientist, Luke Xie, lukexie@amazon.com
Senior Product Manager, Evan Chen, evchen@amazon.com
Applied Science Manager, Daniel Cociorva, cociorva@amazon.com


## Motivation
- Abuse detection should focus on intent detection. The key is to find if "customers lie about their experience."
- In order to detect lying, we need to know what they say.


## Processing and Inference Steps

![[abuse_polygraph_method_pipeline.png]]

Highlights:
- Two main design choices in the plan are *tagging method* and *model algorithm*. 
	- For tagging, we would need to explore the data to understand what is the best way to tell apart deception statement from truth. Current solution used the known DNR tagging.
	  
	- In the Deception Detection module, we only used the BERT encoder.
	  
- Main tasks in processing
	- Identify participants
	- Filter out non-concession related contacts
	- Filter out non-human contacts
	- Remove CAP policy related contacts such as incident report, police report. 
	- Keep only customer sentence
	- Remove agent name in customer contact


## Result Hightlights

- **Data**: chat transcript (rawTranscript) with human agent conversations, removing contacts with “incident report” or “police report” to avoid CAP related leakage.

- **Label definition:**  
	- Bad contacts: all concession *related* contacts from *accounts closed* for concession abuse.
	- Good contacts (Very Low Risk population): concession related contacts from accounts with 
		- *longer than 2 year tenure*, 
		- placed *more than 10 orders worth over $1000*, 
		- *only 1 concession*, *less than 5% SI*, and 
		- in *normal status*.
	- Good contacts for all non-closed accounts
	  
	  
- **Algoritm**: fine tuned RoBERTa.

- **Performance** on hold out dataset: 0.84 AUC, excluding contacts already signaled to CAP.  

- **Manual Review**  
	- **CAP agents**: We also shared 500 contacts that have the highest scores from the out of time test data with CAP agents to perform offline audit. Result shows **55%** of the accounts deemed risky/abusive by CAP agents.  

	- **ARI agents**: ARI audit shows “it is observed that **76%** of the cases demonstrated abusive contact transcripts and were enforceable under current MAA guidelines.”


![[polygraph_roc.jpg]]



## Which stage to deploy

We are looking for deployment in Refund Interception (RI)



## Progress Updates


| Time       | Content                                                                                                                                                                                                                                          | Progress    |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- |
| 06/26/2023 | Contact with AIT team on data useage                                                                                                                                                                                                             | Done        |
| 06/28/2023 | Pulling DNR tag                                                                                                                                                                                                                                  | Done        |
| 06/29/2023 | 1. discuss data input/preprocess<br>2. unsupervised learning vs. fine-tuning with labels directly<br>3. downstream task evaluation.                                                                                                              | Done        |
| 07/05/2023 | Cradle jobs to download transcripts with Abuse labels                                                                                                                                                                                            | Done        |
| 07/06/2023 | 1. Chat data is **agent-dominant** conversation, i.e., they will follow SOPs to deal with customer’s cases.<br><br>2. TODO: focus on extract embedding from abusers’ data.<br>3. Cheng get 5 millions labels (one year). 1.4 millions chat-data. | Done        |
| 07/13/2023 | clarify the data preprocessing; Email data without attachment is been backfilled                                                                                                                                                                 | Done        |
| 9/22/2023  | Finished initial prototype model build on chat data.                                                                                                                                                                                             | Done        |
| 10/5/2023  | Pull a new dataset and rebuild the model                                                                                                                                                                                                         | Done        |
| 11/16/2023 | Draft Project Proposal                                                                                                                                                                                                                           | Done        |
| 2/14/2024  | Latest audit results by ARI on one day (12/6/2023) top 50 scored contacts                                                                                                                                                                        | Done        |
| 2/15/2024  | Working on deploying offline model via JUMICS;<br>Completed <br>- Kinesis stream creation<br>- Intent creation: **NA_BUYER_ABUSE_CONTACT_EVAL**<br><br>Ongoing tasks:<br>- Variable onboarding<br>- MDS bucket creation                          | Done        |
| 2/28/2024  | Completed <br>- Variable onboarding<br> - MDS bucket creation<br><br>In Progress<br>- Model onboarding                                                                                                                                           | In Progress |
|            |                                                                                                                                                                                                                                                  |             |


----
## Quip doc:

- [Project Proposal: Abuse Polygraph](https://quip-amazon.com/bgsNAXHHzPAc)
- [quip design doc](https://quip-amazon.com/TbzrAosEuA2j/Science-Experiment-Review-Abuse-Polygraph)   
- Tracking the progress of the project and the results [quip result](https://quip-amazon.com/Za7TAR1L2RSw/Abuse-Polygraph)  
- [quip summary report](https://quip-amazon.com/bgsNAXHHzPAc/Project-Proposal-Abuse-Polygraph)
- Working on deploying offline model via JUMICS: [JUMICS Onboarding Plan - Polygraph](https://quip-amazon.com/TxcBArVPZGsw)
