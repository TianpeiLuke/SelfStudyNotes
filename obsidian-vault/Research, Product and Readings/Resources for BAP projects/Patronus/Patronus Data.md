---
tags:
  - project
  - reference
  - wiki
  - customer_service_contact
aliases:
  - 0804csdpia00
date of note: 2024-02-27
name: Global Data Protection Impact Assessment for CS data digestion
---

- [Patronus Data internal wiki](https://w.amazon.com/bin/view/Perfect_Order_Experience_Tech/DSPE/Patronus/Onboarding/#HPatronusData)
- [HeartBeat internal wiki](https://w.amazon.com/bin/view/Heartbeat/Home/)

## Data Sources

- Ingestion Customer Feedback Sources that Patronus augments
    - Realtime
        - Heartbeat Sources: See [[HeartBeat Entry Point]]
            - [SellerFeedback](https://w.amazon.com/index.php/CSTech/Heartbeat/DataIngestion/Sources/SellerFeedback)
            - [Reviews](https://w.amazon.com/index.php/CSTech/Heartbeat/DataIngestion/Sources/ProductReviewsv2)
            - [Customer Service Contacts](https://w.amazon.com/index.php/CSTech/Heartbeat/DataIngestion/Sources/CustomerServiceContacts)
            - [Returns](https://w.amazon.com/bin/view/CSTech/Heartbeat/DataIngestion/Sources/OnlineReturnCenterCommentsv2)
        - [MYR Returns](https://w.amazon.com/bin/view/MYR)
    - BatchS
        - [BBC](https://dryad.amazon.com/#/CTPS-DSPE/profiles/f5d0d9f4-eac4-4b5b-8ff2-c8e455f9622d)
        - [Claims](https://dryad.amazon.com/#/CTPS-DSPE/profiles/b12653bf-3591-4bbb-9c27-21fda3e611a9)

- This is a sample of a public source (reviews) that Patronus has augmented: [https://paste.amazon.com/show/aiwilson/1652376086](https://paste.amazon.com/show/aiwilson/1652376086)
- [[Sample Patronus record]]

>[!info] 
>Check on the internl wiki for HeartBeat service within **Voice of Customer Framework**

## Statistics on Data Volume

| **Feedback Source** | **Ingestion Source** | **Public/Private Confidentiality (RED)** | **Can contain PII Data** | **Rough 30 Day Volume (with order-fan out)** | **Rough Percentage with Respect to Total Traffic** |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Customer Service Contacts | Heartbeat | Private | Y | 12MM | 14% |
| Returns | Heartbeat | Private | Y | 60MM | 70% |
| Reviews | Heartbeat | Public | N | 2MM | 2.5% |
| Seller Feedback | Heartbeat | Public | N | 500k | 0.5% |
| Buyer Seller Messaging | Andes | Private | Y | 4.5MM | 5.5% |
| Claims | EDX | Private | Y | 350k | 0.4% |
| MYR Returns | SNS | Private | Y | 5.5MM | 6.5% |

## Accessing Patronus Data

[[Patronus Data Access]]