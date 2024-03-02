---
tags:
  - data_sources
  - data_digestion
aliases: 
date of note: 2024-03-01
---
## BSM Ingestion Pipeline

### Design via LEO


![[bsm_leo_real_ingestion.jpg]]

#### Low-level Proposed State Details

1. SNS - Data topic which will contain BSM message metadata in realtime
	- Owned by the Hoplite team
	  
2. LEO - Workflow to execute to process BSM messages
	1. Check Message Status
	2. Extract information from SNS
	3. Deobfuscate CustomerID/marketplaceID
	4. Deduplication DynamoDB mechanism
	5. Get Message Body
	6. Preprocess Message Body
	7. Write to MDS
	8. 
3. MDS - Data storage system we will be using to store message information and message body
	1. Separated by MessageID
	2. Fields:
		- Order information
		- Seller and Buyer information
		- Message information
		- Message body
		- More information about current MDS variables: [TRMSDataStreams/region_na/bsm_orders/bsm_consume_events.py](https://code.amazon.com/packages/TRMSDataStreams/blobs/451df6e0723e2d3cc0e922761d4463589008a388/--/src/trms_data_streams/region_na/bsm_orders/bsm_consume_events.py#L8-L29)
		- Extracted Shipping Track ID and Address
		- Provided Shipping Track ID and Address
		  
4. OTF - Variable platform which will retrieve and calculate variables using data stored in MDS
	- Order-level datasheet
	- Customer-level datasheet
	- More information about current OTF variables used: [AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/BSM_OTF_Variables/#HBSMRealtimedatastreamanddatasheet](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/BSM_OTF_Variables/#HBSMRealtimedatastreamanddatasheet)


### LEO Recipe Operations

1. Check message status; Only accept “SENT” and “SUPPRESSED” messages
2. Extract information from SNS (Common, exists) (Regex extract)
	- Identify between buyer and seller
	- Obtain CustomerID and MarketplaceID  [https://datacentral.a2z.com/cradle/?mons_redirect=sign_in&mons_redirect=sign_in&mons_redirect=sign_in&mons_redirect=sign_in#/BRP-ML-Abuse/profiles/166743d0-cec8-4848-8c4f-d5d23193ccba](https://datacentral.a2z.com/cradle/?mons_redirect=sign_in&mons_redirect=sign_in&mons_redirect=sign_in&mons_redirect=sign_in#/BRP-ML-Abuse/profiles/166743d0-cec8-4848-8c4f-d5d23193ccba)
	- extract ShipTrack id and Physical address:   
		- POE team has similar work, their [python code](https://code.amazon.com/packages/BSMInformationExtraction/trees/mainline) and [java code](https://code.amazon.com/reviews/CR-65716698/revisions/2)
3. Deobfuscate CustomerID/MarketplaceID (Common, does not exist)
	- In progress work, will be done by [Shashaank Kumar Jee Bomule](https://quip-amazon.com/IIZ9EA5hOfD)
	- Filter out messages that are in marketplaces we are uninterested in. 
4. Get Message Body (Custom, does not exist)
	- **Message body is not part of SNS**, this requires a separate **[library ACPMessageAccessInterface](https://w.amazon.com/bin/view/BSMP/AnonymousCommunicationPlatform/APIs/ACPMessageAccessInterface-3.0/) to access.**
5. Dedupe check mechanism (Custom, does not exist)
	- Write and put to DynamoDB ThreadID (key) and MessageID list (value)
	- Buyer messages
		- Add ThreadID and MessageID to DynamoDB. If ThreadID already exists, append MessageID to the value
	- Seller messages
		- Check if ThreadID already exists in DynamoDB
			- Disregard the message if threadID does not exist. This means the buyer has not initiated a message with the seller
		- Append MessageID to the list
6. Preprocess message body (Custom, does not exist)
	- Remove excess information, only keep main message body
	- Extract Shipping Track ID and Address; if information provided 
7. Write to MDS (Common, exists)
8. Dedupe add mechanism (Custom, does not exist)
	- After message is processed correctly, add to dedupe table


### Storage and Schema

- MDS location: 
[https://datacentral.a2z.com/edx/providers/cmls-raw-data/subjects/buyerabuse-bsm](https://datacentral.a2z.com/edx/providers/cmls-raw-data/subjects/buyerabuse-bsm) 

- MDS service name: **BuyerAbuseBSM**

- List of variables: https://unified-ml-catalog.ctps.amazon.dev/query-mds-signature?region=NA&datasetName=BuyerAbuseBSM&partitionID=0
  
```
[arrival_date,
attachment_num,
body_type,
customerId,
entry_point,
extractedAsin,
extractedEmailAddress,
extractedOrderId,
extractedShipTrack,
extractedUrl,
from_email_address,
last_update_date,
marketplaceId,
messageId,
message_body,
message_status,
message_type,
objectId,
orderId,
receipient_customerId,
recipient_email_address,
recipient_role,
sender_customerId,
sender_role,
status_effective_date,
subject,
threadId,
topic_id,
transactionDate]
```



-----------
##  Recommended Notes

- Check [quip doc](https://quip-amazon.com/9NhZAvroIdUv/Buyer-Abuse-Buyer-Seller-Messaging-BSM) from Mitchell Zhang (mitzhang@amazon.com) on BSM data ingestion pipeline.
