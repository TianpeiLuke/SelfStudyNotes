---
tags:
  - project
  - abuse_slip_box
aliases: 
date of note: 2024-02-22
---
***Slip-box (Zettelkasten)*** as a personal knowledge management system provides a complementary view on how we can organize the various form of text information available in the team. 

- Compare to the BAP knowledge management system [[Issues of BAP data management system]]

The proposed **Abuse Slip box** would thus mitigate above issues by borrowing the main features from the *Zettelkasten method*: 

- **No raw data is stored in abuse slip box**. We need to **_paraphrase_** _and_ **_summarize_** the original text/tabular data into **atomic** notes following a **standardized** format. The process of summarization and paraphrasing allows us to remove redundant, irrelevant information for original text. It also reduces the cost due to inconsistent format when merging information from multiple sources. From higher perspectives, the dialogues from Customer Service Contacts or BSM, the annotations from human investigators, the procedures and descriptions in SOPs are treated the same way as an atomic piece of information related to the investigation of concession.
  
- Abuse slip box is a **central knowledge database** for “**_symptom_** _and_ **_treatment_**.” while the models (e.g. LLMs) and SOPs are used for **_diagnose._** Here we use the terminology from medical service as analogy. 

	- “_symptom_” describes the customer’s behavior, including order-related tabular information, the reason of concession, shipment status, the customer contacts requesting the concessions etc. Past “symptoms” are aggregated in customer-level. 
	  
	- “_diagnose_” describes the process of identifying an abuse case. An example of diagnose process is the predetermined SOPs for ARI. This step-by-step procedure encodes the reasoning process behind the risk evaluation. The RMP rules that were triggered for a given concession order can also be considered as part of a diagnose process, which indicates which symptom links to which categorization and actions (treatments). The chain-of-thought reasoning in LLM provides a good demonstration of risk diagnose. The reason process itself is a step-by-step question-and-answering. The question as well as the answer can be used in the diagnose.
	  
	- “_treatment_” describes the output of an abuse evaluation system including the actions taken on the customer and the human (ARI, CReturn, CS agents, Seller etc.) annotations on the action. Text output may also be available describing the treatment, e.g. in email referral workflow. The idea of slip box in abuse prevention is to keep all relevant information in one place so that at inference time model do not need to search externally.  
	
- **Notes in abuse slip box are connected** by **comparing** their _contents_, their _topics_, their customer/order ids, and their evaluation workflows. When a new note is created, we search notes with same order_id/customer_id, notes with similar context, notes with same workflow. Then we connect new notes with old ones accordingly.


-----------
##  Recommended Notes

- See the features of *Zettelkasten* [[The definitive feature of Zettelkasten]]
-  [[How to Automatically Compare Notes]]