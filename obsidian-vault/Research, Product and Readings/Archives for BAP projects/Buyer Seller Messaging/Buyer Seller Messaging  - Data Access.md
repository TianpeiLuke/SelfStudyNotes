---
tags:
  - data_sources
  - data_access
  - buyer_seller_messaging
aliases:
  - 1001bsm02
date of note: 2024-03-01
---
## Overview

Buyer seller message(BSM) data is available on Kinesis, EDX and Redshift (Internal). Depending on the usage case, there are different ways to query BSM data.

- **Kinesis** (***RealTime Stream Data***): BSM meta data is available on Kinesis. Kinesis has both finalized message(message state is finalized) and transient messages( message is still in processing). Message body is not available on Kinesis. 

- **EDX** (***Aggregated Daily Data***) Finalized message meta data, message body, message event, customer event are available in EDX

- **EDX** (***Raw BSM Data***) Raw BSM message meta data, message body, message event, customer event without flatten or aggregation are available in EDX

- **Redshift** (***Aggregated Daily Data***) Finalized message meta data and message event are available in Redshift for internal operations/business tracking.

## Common Terms

- **Message Meta Data** Message meta data contains a list of attributes of messages, (eg, sender and recipient information(customer id, role, marketplace), message type(webform or email)....), meta data doesn't have the actual message content

- **Message Body** This is the actual message content(**red data**)

- **Message State** Only messages with finalized message state are available in EDX. Transient states(eg. PERSISTED) messages will not be visible in EDX. Here is the list of message states, The last filed(true or false) in the enum indicates whether a message state is terminal or not. [^1][^2]

- **Topic Id** We use topic id to track what is message about(eg, cancel order or shipping. [^3]

- **EntryPoint** We use entry point to track where is the message originated(eg, seller central, retail website). [^4]

- **Party** We define a party as "Encrypted CustomerId":"Encrypted MarketplaceId":"Customer Role" (eg A1AJ8Y8HP6WW0U:AAHKV2X7AFYLW:SELLER)

- **Decrypt customer id/market place id in Dryad job** In Dryad scala script: amzn_id_decrypt(Customer_id) as Customer_id


## Data Access

### EDX

BSM meta data and message body are also available in EDX([https://edx.corp.amazon.com/providers/bsm-prod](https://edx.corp.amazon.com/providers/bsm-prod)) which is accessible via dryad([https://dryad.amazon.com/](https://dryad.amazon.com/)) jobs. 

#### Dataset

[https://edx.corp.amazon.com/providers/bsm-prod](https://edx.corp.amazon.com/providers/bsm-prod)

**For BSM data consumer teams:**

- **party-thread-daily** This dataset contains details about the thread between two parties (sender and receiver) on daily basis.

- **thread-message-daily** This dataset contains details about the actual messages in a thread grouped per day (excluding message body). All the data about messages is present in this data set

- **thread-message-with-bodies-daily** This dataset contains details about the actual messages in a thread grouped per day including message body. All the data about messages is present in this data set

- **party-attribute-daily-data** This dataset contains attributes and events about the party (sender or receiver). example event is, CUSTOMER_FLAG event with attribute of SPAM_MESSAGE

- **thread-message-event-daily-data** This dataset contains events about the messages (eg: message flagged as spam by ERS, or This message was auto-replied, or this message requires response)

#### EDX ARN

- **ThreadMessage**: arn:amazon:edx:iad::manifest/bsm-prod/thread-message-daily/thread-message-daily-data/["prod",Region(CN,FE,NA,EU),Date]
- **PartyThread**: arn:amazon:edx:iad::manifest/bsm-prod/party-thread-daily/party-thread-daily-data/["prod",Region(CN,FE,NA,EU),Date]
- **ThreadMessageWithBodies**:  arn:amazon:edx:iad::manifest/bsm-prod/thread-message-with-bodies-daily/thread-message-with-bodies-daily-data/["prod",Region(CN,FE,NA,EU),Date]
- **PartyAttribute**: arn:amazon:edx:iad::manifest/bsm-prod/party-attribute-daily/party-attribute-daily-data/["prod",Region(CN,FE,NA,EU),Date]


>[!Note]
>
> - BAP team consumes **thread-message-with-bodies-daily**: [edx link](https://datacentral.a2z.com/edx/providers/bsm-prod/subjects/thread-message-with-bodies-daily/datasets/thread-message-with-bodies-daily-data)
> - Check [[Buyer Seller Messaging  - Message Schema and Field Definitions]]

#### Schema

Here is our data schema:

- **PartyThread**: [PartyThread EDX schema](https://edx-service.amazon.com/schemata/bsm-prod/51dcdec982754621a201a7497df2db2f)

- **ThreadMessage**: [ThreadMessage EDX schema](https://edx-service.amazon.com/schemata/bsm-prod/aa8b7c2949c8411e8232f1ac8e766c04)

- **ThreadMessageWithBodies**: [ThreadMessageWithBodies EDX schema](https://edx-service.amazon.com/schemata/bsm-prod/9876a44398a54137b929bc7469e733a4)

- **PartyAttribute**: [PartyAttribute EDX schema](https://edx-service.amazon.com/schemata/bsm-prod/b2d46d4fcd954082aa7e4518808a2f68)



>[!info]
> **How to Identify Latest EDX Schema:**
> 
> - Using EDXClient:
> 
> 	1. List parcel under Dataset
> 	2. Find the manifest with most recent modification_timestamp
> 	3. Get Schema for the latest mainfest
> 
> - Using EDX UI:
>     1. Find the most recent manifest on [https://edx-service.amazon.com/manifestmetadata/{Your_Provider}/{Your_Subject}/{Your_Dateset}?range_start=](https://edx-service.amazon.com/manifestmetadata/%7BYour_Provider%7D/%7BYour_Subject%7D/%7BYour_Dateset%7D?range_start=)[{Key1},{Key2},{Date_Key}]&range_end=[{Key1},{Key2},{Date_Key_Max}]
>         - Example: [https://edx-service.amazon.com/manifestmetadata/bsm-prod/thread-message-daily/thread-message-daily-data?range_start=](https://edx-service.amazon.com/manifestmetadata/bsm-prod/thread-message-daily/thread-message-daily-data?range_start=)[%22prod%22,%22CN%22,2018-03-04]&range_end=[%22prod%22,%22CN%22,2018-03-07]]
>     2. Find the schema_name for last parcel
>     3. Retrieve the EDX schema at [](https://edx-service.amazon.com/schemata/%7BYour_Provider%7D/%7Bschema_name%7D)[https://edx-service.amazon.com/schemata/{Your_Provider}/{schema_name}](https://edx-service.amazon.com/schemata/%7BYour_Provider%7D/%7Bschema_name%7D)
>         - Example: [https://edx-service.amazon.com/schemata/bsm-prod/17feda614a2344bcb50d0cebd067cea9](https://edx-service.amazon.com/schemata/bsm-prod/17feda614a2344bcb50d0cebd067cea9)

### Kinesis

- Kinesis only has only message meta data, ***message body is not on Kinesis***
- Kinesis has message meta data in all states including finalized and non-finalized message states, the stream data is directly from Dynamo



## New Consumer Onboarding

Please submit a SIM using this [template](https://sim.amazon.com/issues/create?template=46829d23-0524-4294-a849-0c2f98c12310)


[^1]: Code for [BBCommunicationMgrConstants](https://code.amazon.com/packages/BBCommunicationMgrConstants/blobs/0fba9bf299fbd1a50db54855c2ff3e811df5dfca/--/src/com/amazon/trms/commMgr/constants/MessageState.java#L121)

[^2]: Our sample code of checking if a message is terminal: [https://code.amazon.com/packages/ACPStreamsWorkers/blobs/99fbe12a6ab3b6dda91be820f100760152d698a4/--/src/com/amazon/acp/streams/processor/kinesis/psng/PSNGProcessor.java#L67](https://code.amazon.com/packages/ACPStreamsWorkers/blobs/99fbe12a6ab3b6dda91be820f100760152d698a4/--/src/com/amazon/acp/streams/processor/kinesis/psng/PSNGProcessor.java#L67)

[^3]: Here is the list of Topic ids: [WebformMessageTopic Code](https://code.amazon.com/packages/BBCommunicationMgrConstants/blobs/c4ef422d0bbdd750cace47a8be1ab1197f545d14/--/src/com/amazon/trms/commMgr/constants/WebformMessageTopic.java#L11); Also see [[Buyer Seller Messaging  - Topic Id]]

[^4]: Here is the list of EntryPoints: [WebformEntryPoint](https://code.amazon.com/packages/BBCommunicationMgrConstants/blobs/2d4c278c7a8f15010e351c5dc7fd2c57c2a6c92f/--/src/com/amazon/trms/commMgr/constants/WebformEntryPoint.java#L17); Also see [[Buyer Seller Messaging  - Entry Point]]


-----------
##  Recommended Notes

- Buyer Seller Messaging service [official wiki](https://www.amazon.com/gp/help/customer/display.html?nodeId=G3JQ9V9LQ8FFMR7W) 
- Contact a 3rd Party Seller [official wiki](https://www.amazon.com/gp/help/customer/display.html?ref_=hp_left_v4_sib&nodeId=GLC8ZMBWMBTR6QZZ)
- BSM Data Consumption  [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/)
- BSM Kinesis stream [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/ConsumerKinesisData/)
- BSM EDX data [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/ConsumeEDXData/)
- BSM Raw EDX data [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/ConsumeRAWEdxData/)