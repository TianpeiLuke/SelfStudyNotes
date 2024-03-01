---
tags:
  - project
  - abuse_slip_box
aliases: 
date of note: 2024-02-22
---
- **Knowledge Management vs. Archive**: Our current existing data management system are essentially ***archives*** of log-files. The purpose of data management is just for storage of evaluated records. Every piece of information is dumped into this black hole of archive which is not designed for quality check, deep dive, let alone for LLM inference. 
  
- **Segregation of Input and Output of Evaluation in Storage**: Data are organized according to the online evaluation workflow: data containing order/customer information are separated from the data containing the manual investigations and data containing abuse definitions and SOPs. This is because the former is treated as a part of the evaluation system (collected at ***Gather** phase* of [[URES workflow]]) and the latter are treated as outside of the evaluation system (human decisions are not considered as part of the evaluation since the evaluation ends with the automated decision including pass and sideline.)
    
	For ML and DS, both input data and output data need to be combined and aggregated to reconstructed the complete information at investigation. Thus information aggregation is complicated, error-prone and time-consuming since the original raw data was not stored in the same place and was not connected during the storage phase.    
	
- **Inconsistent Data Format**: Various type of data and their format can be seen in [[Buyer Abuse Prevention System - Data]]
	  
- 






, 



-----------
##  Recommended Notes