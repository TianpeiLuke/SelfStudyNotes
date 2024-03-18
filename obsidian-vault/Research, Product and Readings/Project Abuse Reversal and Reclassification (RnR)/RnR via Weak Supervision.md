---
tags:
  - reversal_reclassification
  - amazon_machine_learning_conference
aliases: 
date of note: 2024-03-06
---
## Problems associated with RnR

[[RnR Background]]

RnR aims at identify non-abusive or incorrectly labeled cases and mitigate its impact on existing system (OTF, Weekly Business Review (WBR),  ML models and rules )

- Problems of concern behind RnR: 
	- concession reason code is noisy and is reversible
	- due to noisy concession reason code, ML label is noisy too. 
	- the reversal flag itself is also noisy.


>[!question]
>Can you summarize the major ML related problems?

- RnR is a use case where *the label definition of ML model is noisy* and *human label provider (buyer, seller, ARIs) are not trustworthy*. 
- RnR is a use case where *the size of labeled samples is not sufficient* to train sophisticated models. 


>[!todo]
>List related questions and check my interest

| Problem Settings                                                                                                                                                                                                                                                                                                                                         | Topic                                                                                                  | Interest?      | Why?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| the training data set is fully labeled with positive and negative labels                                                                                                                                                                                                                                                                                 | <br>- *supervised learning*                                                                            | Maybe          | By far, the RnR in production do not make additional efforts to account for sample bias and label noise. Both exists in the training set but we choose a simple path to launch the model in production without assuming that. This brings trouble in maintenance and causes drop in precision after launch.                                                                                                                                                                                                                                  |
| the labeled training set is limited but the label is ground truth;                                                                                                                                                                                                                                                                                       | - *semi-supervised learning.*                                                                          | No             | SSL tends to not give good performance given that abuse positive tag is limited and the difference between the abuse and non-abuse in unlabeled population is not clear                                                                                                                                                                                                                                                                                                                                                                      |
| there exists label noise in the training samples, possibly from adversarial attacks, or from noisy labeler; usually there is only one label source                                                                                                                                                                                                       | - *noise-tolerate learning*, <br>- *robust learning*,<br>- *adversarial learning*                      | No             | most of noise-tolerate learning models are not applicable in real life applications. Also in order to test performance, it requires knowledge on ground truth and a set of correctly labeled "golden standard"<br><br>                                                                                                                                                                                                                                                                                                                       |
| there only exists positive labels; the rest are all unlabeled                                                                                                                                                                                                                                                                                            | - *anomaly detection*; <br>- *one-class classification*;<br>- *traditional weakly supervised learning* | No             | The techniques assume that there exists little prior knowledge on the incoming target. This is not true in RnR. RnR has clear definition of what abuse we want to find. The issue is that the abuse target is not measured correctly                                                                                                                                                                                                                                                                                                         |
| the labeled training set is limited. But we can ask for more labels given a budget. Labels are considered trustworthy.                                                                                                                                                                                                                                   | - *active learning*                                                                                    | No             | Active learning focus on sampling strategies which are usually ad-hoc and application dependent. Moreover, random sampling has advantages when the number of label requests increases since the ML model offers theoretical guarantee for large number of random samples. Random sampling balance the coverage and efficiency very well. Hard to beat them without prior assumption on the data distribution and underlying structures.                                                                                                      |
| the labeled training set is from a different distribution as compared to test set.  <br><br>This may due to change of distribution on newly acquired data, such as <br>- adversarial attacks, <br>- change of labeling logics (such as SOP change or better training in BAP)                                                                             | - *transfer learning*                                                                                  | Maybe, not now | Transfer learning for a different problem. RnR did not assume that there exists a shift on the abuse definition nor did it assume that there exists a transition within the concession reason. Although the dynamic nature of BAP fit such assumption we do not explicitly explore that direction.<br><br>This is a relevant question, though, in production and maintenance since later we found that the definition of reversal flags have changed and also ARI has been better trained on the task. Thus the labeling logic would change. |
| the target definition expands over time and model need to progressively fine-tune with limited newly added samples to cover both new and old concepts. The issue for progressive fine-tune is that the newly learned knowledge would overwrite the old knowledge, causing the entire system loss capability to identify previous trained target as well. | - *continual learning*                                                                                 | No             | RnR is not about progressive fine-tuning nor about stop *catastrophic forgetting*. RnR project currently focuses on a successful one-time launch.                                                                                                                                                                                                                                                                                                                                                                                            |
|                                                                                                                                                                                                                                                                                                                                                          |                                                                                                        |                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## Programmatic Weak Supervision 

>[!todo]
>List settings from PWS and its relationship to RnR.

| PWS settings                                                                 | Related to RnR? | Why?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------------------------------------------------------------------------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **assumption**: there are limited labeled training samples                   | Yes             | RnR only has 20,000 samples WW. For each region is even smaller.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **assumption**: there are both positive labels and negative labels.          | Yes             | RnR positive label: reversible flag = 1; => buyer is NOT at fault. <br>RnR negative label: reversible flag = 1; => true DNR, true MDR, true FLR etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **assumption**: the label obtained are not trustworthy.                      | Yes             | in audit reviews, it is known that the investigator miss rate in RnR manual investigation ranges from 10% to 50%.<br><br>In general, for all BAP workflows, manual investigation has error rate of about 10%. Similarly, we found that rule-based Abuse definition does not completely fit the SOP for human investigation.  **Untrusted labels has been the number 1 concerns behind BAP.** This is why this point is the point that excites me.<br><br>In fact, the proposal of RnR is due to lack of trust on abuse labels for ML. Corrupted reason code is just one example but could be more than that. <br><br>Lack of trust on human labels is the motivation behind the launch of Action Taking System (ATS) [[Action Taking System Entry Point]] |
| **assumption**: there exists domain knowledge experts that can provide label | Yes             | Most BAP applications have specific definition on abuse behaviors, includes DNR, MDR, NSR, FLR, MAA etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **assumption**: there exists multiple sources that can provide label         | Yes             | BAP in general has the following sources of label:<br>- **Standard Operating Procedure (SOP)** for human investigator<br>- **Rule-based Abuse Definition** from product team.<br>- More rules from **Rule Management Platform (RMP)**<br>- **Customer Contacts Sources**: Buyer Seller Messaging (BSM)<br>- Existing **Abuse models for DNR, NOTR** etc                                                                                                                                                                                                                                                                                                                                                                                                   |
|                                                                              |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |







- How to identify and classify events using a thread of email exchanges between buyer and seller?
	- Treat label from human investigator as ground truth. Train a multi-modal encoder + classifier to encode text and tabular information and predict target label;
	- Same as [[BSM A-to-Z claim abuse detection]]
	  
- **Issue**: 
	- Evidence suggests that label from ARI annotations on RnR itself has up to 50% error rate.
	- The total number of annotated samples is only about 20,000 WW, (about 60% of them are from US only). So for EU and FE region, we do not have enough training data
	  
- How to build a model under unreliable label?
	- do we have enough fully annotated and trustworthy labels? (*supervised learning* problem?)
		- We do not.
	- do we have a large subset of annotated and trustworthy labels? (*semi-supervised learning* problem?)
		- It depends on how much is enough. But the quality of label is questionable and it is collected throughout 2 years time period. 
		- The policy on RnR definition has changed recently as well.
	- do we have multiple sources to provide "ok" labels?  (*weakly supervised learning* problem)
		- 
			- programmatically synthesizing training labels from multiple label functions
			-
			- 
			- what is **labeling function**:
				- rules, regular expression
				- XGBoost models from DNR and NOTR
				- ARI annotations
		- keyword: *Weak supervised*. 
		- how to combine multiple weak labels 
			- label model or joint model?
			- Can we train end-to-end model that combine outputs of multiple label functions to build a robust classifier. 
		- What is LLM role in weak supervision?
			- LLM do not have domain expertise but it has very strong reasoning, 
			- we can have prompt-based label functions. Each label function corresponding to one prompt and use multiple prompt to generate yes or no answers to the example. 
	- do we have labels at all? an *unsupervised learning* problem?







-----------
##  Recommended Notes

- Survey on *Programmatic Weak Supervision* [[zhangSurveyProgrammaticWeak2022]]; 
- Original paper  data programming [[ratnerDataProgrammingCreating2016]]
- Snorkel as PWS tool [[ratnerSnorkelRapidTraining2020]]