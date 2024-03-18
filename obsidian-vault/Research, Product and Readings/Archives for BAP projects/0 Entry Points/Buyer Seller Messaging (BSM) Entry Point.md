---
tags:
  - data_sources
  - data_digestion
  - data_pipeline
  - entry_point
  - buyer_seller_messaging
aliases:
  - 1001bsm0
date of note: 2024-02-28
name: Buyer Seller Messaging
author:
---

## Background

[[Buyer Seller Messaging  - Background]]

**Buyer Seller Messaging (BSM)** is an important tool for communication between buyer and seller, where buyer receive concessions from seller. It is thus important for [Buyer Abuse Prevention team](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/) to understand what happens during the communications and to identify suspicious activities. 

It is known that high risk abusers can be distinguished from normal customer based on their way of communications. For instance, The Customer Service (CS) received hundreds of thousands of chats and emails from buyer every day and an experienced CS specialist is able to identify suspicious emails to refer to us. In artificial intelligence and machine learning community, identifying suspicious activities from email conversation is an active research area, which involves **Anomaly Detection, Natural Language Understanding (NLU)**, **Information Extraction (IE)** and **Deep Learning with Attention mechanisms** etc.

For *MFN* orders, sellers grant concession themselves. It is expected that buyer and seller would negotiate and reach agreement before refund/return is issued. Otherwise, Amazon provides buyer an additional option to file an *[A-to-z Guarantee](https://www.amazon.com/gp/help/customer/display.html?nodeId=GQ37ZCNECJKTFYQV) Claim*, asking Amazon to adjudicate the issue and grant/deny refund on behalf of seller. 

**Buyer Seller Messaging (BSM)** platform is the main platform for buyer and seller communication in MFN space. It is thus expected that BSM includes additional context information behind the concession requests such as concession reason, shipment or delivery status. Among BSM communications, there exist suspicious emails with abnormal patterns. These patterns are also indicator of abusive behavior at contact time. 

## Owner of BSM Platform

[[Buyer Seller Messaging  - Seller CS team]]

## Access BSM data

Buyer seller message(BSM) data is available on Kinesis, EDX and Redshift (Internal). Depending on the usage case, there are different ways to query BSM data.

- **Kinesis** (***RealTime Stream Data***): BSM meta data is available on Kinesis. Kinesis has both finalized message(message state is finalized) and transient messages( message is still in processing). Message body is not available on Kinesis. 

- **EDX** (***Aggregated Daily Data***) Finalized message meta data, message body, message event, customer event are available in EDX

- **EDX** (***Raw BSM Data***) Raw BSM message meta data, message body, message event, customer event without flatten or aggregation are available in EDX. This is near real-time BSM data in EDX. 

- **Redshift** (***Aggregated Daily Data***) Finalized message meta data and message event are available in Redshift for internal operations/business tracking.

Key take-aways:
- BAP consumes ***EDX Raw BSM data*** in near real time; [[Buyer Seller Messaging  - Data Ingestion Real-time]]
- Also we use *EDX Aggregated Daily Data* to build offline data ingestion and inference system. [[Buyer Seller Messaging  - Data Ingestion Batch]]
- *EDX Aggregated Daily Data* are also used in OTF variable creation.  
- Check [[Buyer Seller Messaging  - Data Access]] for more information on Data Access


## BSM Data Digestion Pipeline

### Offline Batch Pipeline

[[Buyer Seller Messaging  - Data Ingestion Batch]]

Owner: Luke Xie (lukexie@amazon.com)
### Real-time Ingestion Pipeline

[[Buyer Seller Messaging  - Data Ingestion Real-time]]

Owner: Mitchell Zhang (mitzhang@amazon.com)


## BSM OTF variables

- BSM OTF real-time message variable: [[Buyer Seller Messaging  - OTF message]]
- BSM OTF aggregate information: [[Buyer Seller Messaging  - OTF aggregated info]]


-----------
##  Recommended Notes

- [Home wiki](https://w.amazon.com/bin/view/SellerCustomerService) for the Seller Customer Service team (Seller CS) who owns the BSM platform. 
- [A-to-z Guarantee](https://www.amazon.com/gp/help/customer/display.html?nodeId=GQ37ZCNECJKTFYQV) : Claim service that allows Amazon adjudicate the refund issue and grant/deny refund on behalf of seller. 
- BSM Data Consumption  [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/)
- [Internal wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/) for BSM for BAP
- Check this [quip](https://quip-amazon.com/9NhZAvroIdUv/Buyer-Abuse-Buyer-Seller-Messaging-BSM) for real-time BSM data digestion pipeline from EDX Raw Data stream via LEO framework. 
- BAP ML projects using BSM: 
	- [[BSM A-to-Z claim abuse detection]]
	- [[Abuse Reversal and Reclassification (RnR)]]
	- [[Threat Abuse Detection in BSM]]