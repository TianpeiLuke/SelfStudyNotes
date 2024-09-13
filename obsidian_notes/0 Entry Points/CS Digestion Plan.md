---
tags:
  - entry_point
  - project
  - data_digestion
  - customer_service_contact
  - data_sources
aliases:
  - 0804csdigestion0
date of note: 2024-02-27
name: CS Data Digestion Plan
---

# Background

- Check projects in BAP that use CS Contact Data in [[Voice of Customer in BAP Entry Point]]
- Check backgrounds, roadmap and projects for NLP in BAP in [Context-Enhanced BAP](https://w.amazon.com/bin/preview/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/BSM_Prods_Roadmap)


# Three Paths to Access CS Contact Data

## Patronus

*Patronus* offers an end-to-end **real-time solution** to digest multiple data streams including CS contact, BSM, and product reviews. Their solution shared the same URES framework as the BAP team. This makes their solution directly accessible to BAP team.  Patronus itself digests data from **HeartBeat Service**

- Check on the Patronus system, data and onboarding process in [[Patronus System Entry Point]]
- Check on Patronus data access in [[Patronus Data Access]]
- **Key** take-away:
	- Patronus contains multiple sources
	- Patronus is **near real-time**
	- Patronus provide text in **sentence level**; 
	- Patronus uses **URES** and GMRA in implementation
	- CSC and Product review data in Patronus is based on HeartBeat [[HeartBeat Entry Point]]
	- HeartBeat removes ***Personal Identification Information (PII)***
	- Patronus requires **no additional legal approval** for onboarding for BAP

- BAP SDE team has taken over the Patronus onboarding process. 
	- Meeting note by Sam [quip](https://quip-amazon.com/xsYKAoNSTCEt/BAP-Patronus-Onboarding)
	- Major Stakeholders: 
		- Patronus SDE:  Ali Wilson aiwilson@amazon.com; 
		- Patronus PM:  Siddiqui, Kazi kazisid@amazon.com;
		- BAP SDE Tech Lead:  Torbett, Patrick torbettp@amazon.com;
		- BAP SDM:  Bauer, Sam sdbauer@amazon.com
		- BAP PM:  Chen, Evan evchen@amazon.com
		  
## CS Neuron team

CS Neuron team owns the ***Junction service*** which allows them to provide us the CS Contact Transcript (Phone, Email and Chat) in **batch mode**.

- Check on the Junction service, data format and access process in [[Junction Service Entry Point]]
- Check on Junction data access [[Junction Data]]
- **Key** take-away:
	- Junction service is **batch** mode. All chat transcripts for **a single contact creation day** are **batched** together in **a single compressed parquet file**. 
	- Junction service provides *daily batched data* within **48 hours after end of the day**
	- In order to get access to Junction service, non-CS team need to reach out the *CS Privacy team* to acquire sign-off for the use case. 
	- CS privacy team requires **the DPIA (Data Protection Impact Assessment)** reviewed by legal PoC 
	- Junction service is the source for AIT team's digestion solution.
	  
- Our Legal PoC:  Wieche, Kayla kwieche@amazon.com; 
- Our Legal Companion:  Bohl, Matthew <mrbohl@amazon.com>
- Our DPIA draft [[0 DPIA template]]

## CS data digested by AIT team

The *Account Integrity Team (AIT)* has built a pipeline that digests the data from *Junction service.*  This pipeline is a part of the infrastructure that supports **the AIT Impersonation Scams (IPS) project.** See [[Impersonation Scams using CS contact]]

- The data ingestion pipeline can be found in [[AIT CS data digestion pipeline Entry Point]]
- **Key** take-away:
	- AIT team ingest CS transcript data via **Junction** [[Junction Service Entry Point]] and **CSQueryService**;
	- The ingestion pipeline is *running in real time* but *the Junction service itself is in batch mode*. See above details in **Junction**.
	- AIT team save the transcript **text** in **S3** while saving the meta fields (order_id, contact_id etc.) as well as **key prefix of S3** to **MDS** under ContREE workflow
	- Scientist **need to use the object key stored in MDS to map S3 object to get the actual transcript**.
	- The S3 bucket and its storage can be used for training purpose. 
	- Both [[Chat MO detection Entry Point]] and [[Abuse Polygraph]] are using this data set for training the first version of model. 
	- By SDE team (EAGLE) managing the ingestion service, AIT is **not able to support long-term use case** for additional BAP use cases
	- By agreement with AIT team, we would gain access to this data given that we have obtained legal approval and reviewed by **CS Neuron team**.  [[Quotes from emails from Eagle team]]
- POC:
	- EAGLE team manager: Wang, Drew, drewwang@amazon.com
	- AIT Scientist in IPS: Yu, Joyce, yujoyce@amazon.com

# Preference

Patronus > AIT team >= CS Neuron





--- 

## Resources

- [Quip doc link](https://quip-amazon.com/nMrDA3TC2lLh/Review-of-CS-Transcript-Digestion-Plan-and-Next-Steps) for CS Data Digestion plan
- [wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_NLP_CSContact/) for Voice of Customer projects in BAP
- Roadmap, and project tracker in Context-Enhanced BAP (COAP) [wiki](https://w.amazon.com/bin/preview/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/BSM_Prods_Roadmap)
- Project [[Abuse Polygraph]]
- Project [[Chat MO detection Entry Point]]
- Overview of CS related projects in BAP [[Voice of Customer in BAP Entry Point]]