---
tags:
  - reversal_reclassification
  - amazon_machine_learning_conference
aliases: 
date of note: 2024-03-06
---
>[!question]
> What are the major concerns behind RnR ? 

- Concession reason code is not trustworthy and is noisy. 
- Abuse definition that use concession reason code is thus noisy. 
- All of BAP systems (variables, metrics, and models) that use Abuse definition are biased toward incorrect label. 


>[!question]
>What is the major ML problem behind the RnR?

RnR is a use case where *the label definition of ML model is noisy* and human label provider (buyer, seller, ARIs) are not trustworthy. 


>[!question]
>What are the additional ML problems behind the RnR?

- *Not enough labeled training samples.* Only 20,000 WW and it has to split to three regions (NA, EU, FE) due to legal constraints. 


>[!question]
> What are the tech challenges behind RnR ? 

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
		- *Programmatic Weak Supervision* [[zhangSurveyProgrammaticWeak2022]]; 
			- programmatically synthesizing training labels from multiple label functions
			- data programming [[ratnerDataProgrammingCreating2016]]
			- snorkel [[ratnerSnorkelRapidTraining2020]]
			- collection of papers [[Programmatic Weak Supervision Literature Entry Point]]
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