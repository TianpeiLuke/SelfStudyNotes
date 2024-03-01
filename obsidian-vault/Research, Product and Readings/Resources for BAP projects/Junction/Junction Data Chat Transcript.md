---
tags:
  - project
  - wiki
  - customer_service_contact
  - reference
aliases:
  - 0804csjunctionchat
date of note: 2024-02-27
name: Junction data chat transcript
---
## Storage

>[!info]
> Chat transcripts can be picked up from the below S3 buckets:
> 
> 1. batched-**chat**-transcript-bucket-prod-na
> 2. batched-**chat**-transcript-bucket-prod-eu
> 3. batched-**chat**-transcript-bucket-prod-fe

>[!info]
> Transcripts (within the above buckets) are grouped by
> 
> 1. Unobfuscated marketplace ID
> 2. Year (YYYY)
> 3. Month (MM)
> 4. Day (DD)
>    
> All chat transcripts for **a single contact creation day** are **batched** together in **a single compressed parquet file**. 

Here's an example of one such batched file - **s3://batched-chat-transcript-bucket-prod-na/1/2022/04/01/part-00000-5d3790b5-db3b-49ae-b6ee-41fb388896d9-c000.gz.parquet**


## Retention Policy

>[!info]
>Chat transcripts are retained for a duration of **180 days**


## Schema

- **contact_id** is a unique identifier for the contact
- **contact_type** is P/C/E, to indicate phone/chat/email
- **creation_date** is the epoch time the contact was created
- **customer_id** is the unique customer identifier used throughout Amazon.
- **marketplace_id** is the unique marketplace identifier for the one that the contact belongs to
- **raw_transcript** contains the raw chat transcript retrieved from CSCaseQueryService (the authoritative source). More details below.
- **agent_annotations** are the raw annotations (free text) entered by the customer service agent handling the contact
- **auto_annotations** are the CS Central added annotations added automatically when certain actions are taken
- **sic_codes** are the agent selected SIC codes when wrapping up the contact. They indicate what the contact was about, and fall into an ontology. The SIC codes are taken from [CommComponents](https://w.amazon.com/bin/view/CommComponents/), component IDs 54, 55, 56, 57
- **customer_order_ids**, are the order IDs associated with the contact. The order IDs are taken from [CommComponents](https://w.amazon.com/bin/view/CommComponents/), component ID 1
- **asins** are the unique identifiers of the products (in the orders) that the customer is contacting about. The asins are taken from [CommComponents](https://w.amazon.com/bin/view/CommComponents/), component ID 2
- **skill_id** is a unique identifier for a grouping that the agent falls into and is representative of the contacts that they are trained to handle.

## Format

1. The transcript is an array of sentence objects (`MESSAGE`) and event objects (`PARTICIPANT_CHANGE`/`TRANSCRIPT_END`). Each sentence is associated with a *timestamp* (UTC epoch).
2. The attributes from the `MESSAGE` objects that might interest you are the **'text'** and **'transcriptText'**. 
	- **'text'** is **human generated**, while 
	- **'transcriptText'** is **bot generated** (there is some nuance to this). 
	- The **'from'** field is an ID which indicates who generated the text.
3. The `PARITICPANT_CHANGE` events indicate when a customer joins the contact, and an agent joins AND leaves the contact (they leave when a transfer to a different agent happens). The **'participantId'** maps to the **'from'** field from the **'MESSAGE'** events

Here's some code to parse the sentences in the raw transcript [[Code Chat Transcript Parser]]


## How soon is batched data available?

>[!info] 
>Daily batched chat transcript data (for a particular day) is available from **within 48 hours after the end of the day**.


