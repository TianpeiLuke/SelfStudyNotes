---
tags:
  - project
  - legal_document
aliases:
  - 0804csdpiadoc00
date of note: 2024-02-27
name: Global Data Protection Impact Assessment for CS data digestion
---

>[!comment]
>* Describe how the Tool works from an operational/customer perspective: Describe which team(s) use the Tool and how customers, interact with the Tool.
>* Describe how the Tool uses, collects, and stores the data, and where the data is hosted/by whom (AWS/third party).


COAP is owned by Buyer Abuse Prevention team and is not intended for either buyer or seller to directly interact with the system. COAP would improve the existing evaluations used to pass or deny refund requests for high risk customers prior to refund distribution as part of our Refund Interception (RI) evaluations as well as our Abuse Risk Investigation workbench.

COAP would be developed to consume the customer contact transcript data as it becomes available, and evaluate the transcript data against an ML model to generate a risk score to be used as an additional feature for the RI evaluation. The AWS Accounts used to store transcript data would be Anvil Certified for processing critical and highly confidential data. The processed data would be stored in Elastic Data eXchange (EDX)_,_ a centralized and secure metadata store for all Amazon data. EDX provide additional security for AWS S3 data storage and it supports critical and highly confidential data. See [wiki](https://w.amazon.com/bin/view/EDX/FAQ#HSecurity) for additional knowledge on the security of EDX storage.

