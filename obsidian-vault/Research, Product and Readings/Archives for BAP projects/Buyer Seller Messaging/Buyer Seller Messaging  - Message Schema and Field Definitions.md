---
tags:
  - data_sources
  - data_format
  - buyer_seller_messaging
aliases:
  - 1001bsm03
date of note: 2024-03-01
---

## BSM EDX data format

BAP BSM [wiki link](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/#HFieldsofinterest)

|                       |                                                                                                                                                                                                                                                                                                                 |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Column Name**       | **Description**                                                                                                                                                                                                                                                                                                 |
| MESSAGE_ID            | Unique id for message                                                                                                                                                                                                                                                                                           |
| THREAD_ID             | Unique id for thread                                                                                                                                                                                                                                                                                            |
| **ORDER**             | Unique id for Order                                                                                                                                                                                                                                                                                             |
| SENDER_CUSTOMER_ID    | Customer id for sender, amzn_id_decrypted from SENDER                                                                                                                                                                                                                                                           |
| SENDER_ROLE           | Role of Sender, i.e. BUYER or SELLER, amzn_id_decrypted from SENDER                                                                                                                                                                                                                                             |
| RECIPIENT_CUSTOMER_ID | Customer id for receipent, amzn_id_decrypted from RECIPIENT                                                                                                                                                                                                                                                     |
| RECIPIENT_ROLE        | Role of recipient, i.e. BUYER or SELLER, amzn_id_decrypted from RECIPIENT                                                                                                                                                                                                                                       |
| **ENTRY_POINT**       | Populated if a web form message. This denotes where in amazon website this message came from. Entry point is the source of message., e.g. CS_CENTRAL, BUYER_MAIL_UI etc. See [https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms](https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms) |
| INCOMING_IP_ADDRESS   | IP address for incoming email message, not always exist                                                                                                                                                                                                                                                         |
| SUBJECT               | Subject of email                                                                                                                                                                                                                                                                                                |
| MESSAGE_TYPE          | Type of message, like Webform                                                                                                                                                                                                                                                                                   |
| **TOPIC_ID**          | ID for Message Topics groups, e.g. WHERES_MY_STUFF_BUYER_TO_SELLER,  PWO_PACKAGE_DIDNT_ARRIVE_REQUEST_REFUND<br><br>See [https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms](https://w.amazon.com/bin/view/BSMP/BSMDataConsumer#Common_Terms)                                                      |
| MESSAGE_STATUS        | Status of message, e.g. SENT, REJECT                                                                                                                                                                                                                                                                            |
| LAST_UPDATED_DATE     | Date of last updated                                                                                                                                                                                                                                                                                            |
| RETRANSMISSION_DATE   | Date of re-transimission                                                                                                                                                                                                                                                                                        |
| STATUS_EFFECTIVE_DATE | Date when status effective                                                                                                                                                                                                                                                                                      |
| FROM_ADDRESS          | Email of sender                                                                                                                                                                                                                                                                                                 |
| RECIPIENT_ADDRESS     | Email of recipient                                                                                                                                                                                                                                                                                              |
| **MESSAGE_BODY**      | Message content, the raw message                                                                                                                                                                                                                                                                                |
| BODY_TYPE             | Type of message body, e.g. EMAIL                                                                                                                                                                                                                                                                                |
| ATTACHMENT_NUM        | Num of attachments                                                                                                                                                                                                                                                                                              |
| ARRIVAL_DATE          | Date when the message arrived                                                                                                                                                                                                                                                                                   |

- Sample data and schema [link](https://edx-service.amazon.com/schemata/bsm-prod/6bf01f42e1044ebbb1967d897c60943d)
- [[Buyer Seller Messaging  - Topic Id]]
- [[Buyer Seller Messaging  - Entry Point]]



## ThreadMessage

BSM EDX data [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/DataDefinition/)

| Column Name          | Description                                                                                                         | Data Format               | Sample Data                                                               | Is Unique Key |
| -------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------- | ------------------------------------------------------------------------- | ------------- |
| MESSAGE_ID           | Message ID                                                                                                          | number                    | 46153535231                                                               | Yes           |
| THREAD_ID            | Thread Id                                                                                                           | number                    | 3460519534776890000                                                       | Yes           |
| ENTRY_POINT          | Populated if a web form message. This denotes where in amazon website this message came from                        | number                    | 18                                                                        | Yes           |
| INCOMING_IP_ADDRESS  | IP address originated                                                                                               | ip address format         | 54.240.27.50                                                              |               |
| SUBJECT              | Subject of the message                                                                                              | string                    | Order delivery inquiry from Amazon customer  (Order: 114-5652017-6650426) |               |
| MESSAGE_TYPE         | one of the two message types (webform or email)                                                                     | string (webform or email) | Webform                                                                   |               |
| TOPIC_ID             | populated if a web form message. This denotes what option was selected closely matching the reason for this message | number                    | 27                                                                        |               |
| MESSAGE_STATUS       | one of 5 statuses of message                                                                                        | string (one of 5 values)  | SENT                                                                      |               |
| FROM_ADDRESS         | from address                                                                                                        | from address              | marinv@dr.com                                                             |               |
| **SENDER**           | sending party                                                                                                       | PARTY                     | ASX10CGBWU6SB:ATVPDKIKX0DER:BUYER                                         |               |
| **RECIPIENT**        | recipient party                                                                                                     | PARTY                     | A3E30TDTV71FVT:ATVPDKIKX0DER:SELLER                                       |               |
| **ORDER**            | order #                                                                                                             | string                    | 114-5652017-6650426                                                       |               |
| **RAW_MESSAGE_BODY** | Raw message body                                                                                                    | null                      | null                                                                      |               |
| RAW_MESSAGE_LENGTH   | size of raw message body                                                                                            | null                      | null                                                                      |               |







-----------
##  Recommended Notes

- Buyer Seller Messaging service [official wiki](https://www.amazon.com/gp/help/customer/display.html?nodeId=G3JQ9V9LQ8FFMR7W) 
- Contact a 3rd Party Seller [official wiki](https://www.amazon.com/gp/help/customer/display.html?ref_=hp_left_v4_sib&nodeId=GLC8ZMBWMBTR6QZZ)
- Check Schema of EDX BSM data in [internal wiki](https://w.amazon.com/bin/view/Hoplite/DataConsumption/DataDefinition/)