---
tags:
  - project
  - buyer_seller_messaging
  - context_enhanced_bap
  - data_access
aliases:
  - 0801bsmatoz00
date of note: 2024-02-28
name: BSM AtoZ abuse detection
author:
---
# Background
[[AtoZ BSM Background]]

Buyer Abuse Prevention (BAP) in the Merchant Fulfillment Network (MFN) is a challenging task in part because third-party sellers, who manage the fulfillment and concessions service, do not share much information with Amazon. This includes critical information such as delivery information, shipment information and contact information. The lack of such context often leads to a significant rise in the difficulty of maintaining a reliable Buyer Abuse Prevention system. 

The Buyer Seller Messaging (a.k.a. **BSM**) platform provides a data source that mitigates the contextual information gap in the traditional BAP effort. 

# Buyer Claim Abuse 

[[AtoZ Abuse Definition]]

The main target for this project is ***the MFN Delivered-Not-Received (DNR) Abuse.*** 

# Data

- BSM text, aggregated in order-level: [[Buyer Seller Messaging  - OTF message]]
- **customer-level features**: 
	- Sugar Index (DNR_SI, AFN_SI, MFN_SI), 
	- `CUSTOMER_{AFN, MFN, DNR}_ORDER_AMOUNT_12M`, `CUST_CLAIMS_UNIT_AMOUNT_12M`
- **refund-level features**:  `REVERSAL_REASON`, 
- **order-level features:**  `ORDER_TOTAL`, `num_messages_per_order`
- **risk score**: PFW DNR model score, PFW NOTR model score
# Model 
[[AtoZ BSM Model]]

On March 2nd 2022, the Buyer Abuse Machine Learning (ML) team launched a new Deep Learning model on the US A-to-Z claims evaluation workflow via **AWS Sagemaker**. The model, referred as **Context-enhanced Convolutional Neural Network (CE-CNN)**, is an **online** binary classification model which predicts whether an incoming claim will result in a claim-level or customer-level enforcement by the Abuse Risk Investigator (ARI) team due to abuse. 

In May 2023, we conducted a comprehensive code refactoring, involving a complete redesign of the data processing pipeline as well as an upgrade and expansion of the existing model structure and launched a new *Multi-modal BERT model*. 


# Inference Pipeline
[[AtoZ BSM Inference Pipeline]]

CE-CNN model was launched in *A-to-Z Claim interception workflow*, a [[URES workflow]] that is triggered after buyer has issued an A-to-Z claim request. A-to-Z Claim interception workflow aims at identifying potential buyer risk in the upcoming claim. If a claim is considered risky or a customer is considered as abusive, then Abuse Risk Investigator (ARI) would deny the claim on behalf of A-to-Z team and take proper enforcements on buyer's account. 


# Monitors and Dashboards

[[AtoZ BSM Monitor and Dashboard]]


# Code

[[AtoZ BSM Code]]


# Contribution

- Traditional BAP uses gradient boosting method for abuse classification. The CE-CNN model is a deep-learning based model launched in online buyer abuse evaluation workflow. 
  
- It is the first use case that consumes customer contact data in real time for buyer abuse evaluation. 
  
- BSM is just one example of text data sources we can consider. Other data sources such as Customer Service (CS) transcripts, buyers’ comments from the Seller Grading workflow, product reviews, email contacts during Evidence Collection are all available for consumption. The introduction of the CE-CNN model paves the way for the future development of other NLU-based models in Buyer Risk Prevention. [[Context-Enhanced BAP (COAP) Entry Point]]





-----------
##  Recommended Notes

- Check BSM data description, access, owner and pipeline in [[Buyer Seller Messaging (BSM) Entry Point]]