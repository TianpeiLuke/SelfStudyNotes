---
tags:
  - project
  - wiki
  - customer_service_contact
  - data_sources
  - data_format
aliases:
  - 1001csjunction00b
date of note: 2024-02-27
name: Junction data
---
## Storage

> [!info]
> Phone transcripts and enrichment data are stored together in daily batches and can be read from the below **S3 buckets**:
> 
> 1. batched-**phone**-transcript-bucket-prod-na
> 2. batched-**phone**-transcript-bucket-prod-eu
> 3. batched-**phone**-transcript-bucket-prod-fe
> 
> The S3 format of a daily batch of transcripts is separated by marketplace and source (`GACD` or `Connect`) and follows the following pattern:
> 
> - GACD FE daily batch example: [s3://batched-phone-transcript-bucket-prod-fe/GACD/6/2023/12/14/](s3://batched-phone-transcript-bucket-prod-fe/GACD/6/2023/12/14/)
> - Connect FE daily batch example: [s3://batched-phone-transcript-bucket-prod-fe/CONNECT/111172/2023/12/09/](s3://batched-phone-transcript-bucket-prod-fe/CONNECT/111172/2023/12/09/)
>    


>[!info]
>
 >Individual phone transcripts can be found under the PhoneTranscript directory grouped by **year, month, day, contactId**.  
 >
 >**Format**: `s3://individual-phone-transcript-bucket-prod-<realm>/PhoneTranscript/YYYY/MM/DD/contactId/randomUUID.json`


Example S3 uri: `s3://individual-phone-transcript-bucket-prod-na/PhoneTranscript/2023/04/20/1048834070865/2bd2233c-e4d9-4647-b8dd-8eb6c11ffa4e.json  

## Retention Policy

> [!info] 
> Daily batches of phone transcripts will be retained for **180 days**

## Schema

Phone transcripts and enrichment data objects share the following attributes:
- **contact_id** is a unique identifier for the contact
- **contact_type** is P/C/E, to indicate phone/chat/email
- **creation_date** is the epoch time the contact was created (identify the UTC date by inputting value [here](https://currentmillis.com/))
- **customer_id** is the unique customer identifier used throughout Amazon (obfuscated)
- **marketplace_id** is the unique marketplace identifier for the one that the contact belongs to
- **transcript_source** is the service that provided the data (EMPATH (VoiceIntelligence) service via an API call to CASE (CSCaseQueryService))
- **customer_order_ids** are the order ids related to the given contact
- **asins** are the Amazon Standard Identification Numbers of the products within the orders of the given contact
- **skill_id** is the unique id of the skill of the agent who handled the contact (obfuscated)
- **resolution_date** is the epoch time the contact was resolved (identify the UTC date by inputting value [here](https://currentmillis.com/))
- **phoneTranscript** true for all phone transcripts, false for all enrichment data objects

**Phone transcripts** contain the following attributes in addition to the ones listed above:

- **transcribed_utterances** is a list of **utterances** from the given contact that include a transcript of what was said, the party who said it (customer or agent), and time of the specific utterance
- **media_leg_id** is the unique id of the particular media leg from the given contact

**Phone enrichment data** objects contain the following attributes in addition to the ones listed above:

- **agent_annotations** are the raw annotations (free text) entered by the customer service agent handling the contact
- **auto_annotations** are the CS Central added annotations added automatically when certain actions are taken
- **sic_codes** are the customer service case identifiers selected by the agent for the given contact

## Sample

- Example of raw phone transcript  [[Sample Raw Unscrubbed Phone Transcript]]
- Example of phone enriched data  [[Sample Phone Enrichment Data]]