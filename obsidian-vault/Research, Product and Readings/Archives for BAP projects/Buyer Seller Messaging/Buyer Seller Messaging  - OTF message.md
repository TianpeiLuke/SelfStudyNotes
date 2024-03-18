---
tags:
  - data_sources
  - data_digestion
  - variable_design
  - buyer_seller_messaging
aliases:
  - 1001bsm04b
date of note: 2024-03-01
---

## BSM OTF aggregated text Data Sheets

- Abuse.[**bsm_message_ids_and_dates_by_order_marketplace_ids**](https://trms-data-analytics-na.amazon.com/orion/datasheets/Abuse.DataSheet.bsm_message_ids_and_dates_by_order_marketplace_ids): Precomputed datasheet for list of message_id, arrival_date on given order: 

| Variable name              | Data type | Descriptions                                                       |
| -------------------------- | --------- | ------------------------------------------------------------------ |
| message_ids_and_dates_list | B         | List of (Message_id, Arrival Date) for given order, marketplace_id |

- Abuse.**[bsm_records_by_messageid_marketplaceid](https://trms-data-analytics-na.amazon.com/orion/datasheets/Abuse.DataSheet.bsm_records_by_messageid_marketplaceid):** Precomputed datasheet for messages

| Variable name           | Data type | Descriptions                                                                                                                                                                                                      |
| ----------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| message_body            | T         | message_body of emails                                                                                                                                                                                            |
| threadId                | T         | Thread ID                                                                                                                                                                                                         |
| orderId                 | T         | Order ID                                                                                                                                                                                                          |
| customerId              | T         | Customer ID                                                                                                                                                                                                       |
| sender_customerId       | T         | Sender Customer ID                                                                                                                                                                                                |
| sender_role             | T         | Sender Role: 'BUYER' or 'SELLER'                                                                                                                                                                                  |
| from_email_address      | T         | Email address of Sender                                                                                                                                                                                           |
| receipient_customerId   | T         | Recipient Customer ID                                                                                                                                                                                             |
| recipient_role          | T         | Recipient Role: 'BUYER' or 'SELLER'                                                                                                                                                                               |
| recipient_email_address | T         | Email address of recipient                                                                                                                                                                                        |
| entry_point             | T         | Entry point is the source of message., e.g. CS_CENTRAL, BUYER_MAIL_UI etc. See [https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms](https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms) |
| subject                 | T         | Email subject                                                                                                                                                                                                     |
| message_type            | T         | 'Email' or 'Webform'                                                                                                                                                                                              |
| topic_id                | N         | See [https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging#HTOPIC_ID](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging#HTOPIC_ID)          |
| message_status          | T         | 'SENT' or 'REJECT', only 'SENT' is considered                                                                                                                                                                     |
| last_update_date        | T         | The latest update date of message, i.e. the date when the message is pulled from EDX                                                                                                                              |
| status_effective_date   | T         | Date when the message status is effective                                                                                                                                                                         |
| message_length          | N         | Number of tokens in the message                                                                                                                                                                                   |
| body_type               | T         | 'web_text' or 'web_html'                                                                                                                                                                                          |
| attachment_num          | N         | Number of Attachment                                                                                                                                                                                              |
| arrival_date            | T         | Message Arrival Date                                                                                                                                                                                              |

- Abuse.**[bsm_message_body_concat_by_order_marketplaceid](https://trms-data-analytics-na.amazon.com/orion/datasheets/Abuse.DataSheet.bsm_message_body_concat_by_order_marketplaceid):** Inline datasheet that retrieve concatenated list of messages for given order

| Variable name                   | Data type | Descriptions                                      |
| ------------------------------- | --------- | ------------------------------------------------- |
| c_message_body_concat_by_order  | T         | The concatenated list of messages for given order |
| n_total_message_length_by_order | N         | The total number of messages for given orders     |
## Design 

![[BSM_OTF_design.png]]






-----------
##  Recommended Notes

- Check [internal wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/deep_Learning_based_classification/batch_inference/) for design and details on BSM Batch digestion and inference system.
- Check [quip doc](https://quip-amazon.com/9NhZAvroIdUv/Buyer-Abuse-Buyer-Seller-Messaging-BSM) from Mitchell Zhang (mitzhang@amazon.com) on BSM data ingestion pipeline.
- Check [internal wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/BSM_OTF_Variables/) for OTF variable design.
