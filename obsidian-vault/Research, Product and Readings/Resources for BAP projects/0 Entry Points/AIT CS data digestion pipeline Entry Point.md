---
tags:
  - project
  - data_access
aliases:
  - 0802csaitdigest00
date of note: 2024-02-28
---
## Background

This pipeline provide the data support the the [[Impersonation Scams using CS contact]]

## Data Ingestion and Format

The data ingestion is a real-time processing of CS transcripts involves sourcing the data as sns events which are loaded as soon as the entire conversation is transcribed from upstream sources (**Junction** and **CSCaseQuery**). 
  
![[ait_cs_pipeline.png]]
*Figure 1. The data ingestion system*

## Data Storage and Format

- **Data Storage** – Since, the transcript size can be greater than 256 KB (SNS Payload limitation), we use s3 bucket (**cstranscriptspayload-prod-**) to store the transcripts and send only the bucketName and objectKey via the sns topic (**CCFTranscripts SNS**) in real-time. The **ContREE workflow ([wiki](https://w.amazon.com/bin/view/CTPS/BRP/AI-RED/services/))** is subscribed to this sns topic and then it uses these pointers to query the s3 bucket and fetch the transcript in real-time. After model evaluation these pointers are ingested to MDS along with model variables as mentioned by Joyce earlier.

- **Data Format** – The bucket that contains all the transcripts ingested from upstream is the one which is mentioned as above. For example if we want chat transcript the key to query would be  – **Chat/marketplaceId/YYYY/MM/DD/RawTranscript/key**


>[!Summary] 
>The meta fields as well as links to the S3 storage for the raw text is stored in MDS name **ContREE-CCF-CSTranscript.** The pointer to S3 path are being published in MDS, the reason being the transcript size can exceed the column limit.


![[ait_storage_system.png]]
*Figure 2. The data ingestion, model evaluation and post processing system*

## Sharing Data with BAP

[[Quotes from emails from Eagle team]]



-----------
##  Recommended Notes