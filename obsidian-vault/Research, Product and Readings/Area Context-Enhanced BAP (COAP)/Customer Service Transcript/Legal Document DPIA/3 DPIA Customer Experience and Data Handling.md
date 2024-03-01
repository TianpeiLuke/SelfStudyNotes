---
tags:
  - project
  - legal_document
aliases:
  - 0804csdpiadoc00
date of note: 2024-02-27
name: Global Data Protection Impact Assessment for CS data digestion
---

>[!quote]
>* Describe how the Tool works from an operational/customer perspective: Describe which team(s) use the Tool and how customers, interact with the Tool.
>* Describe how the Tool uses, collects, and stores the data, and where the data is hosted/by whom (AWS/third party).


system overview: how are we using the sytem to train, inference and evaluation 


COAP is owned by Buyer Abuse Prevention team. It is not intended for either buyer or seller to directly interact with the system. Instead, buyer and seller would maintain their ordinary order, refund operations without noticing the existence of the system. The evaluation result of the system would affect some customer's refund process as they may experience delayed or cancelled refunds due to their identified high risk based on their history on Amazon. Such prevention mechanism already exists before COAP. 

COAP would consume the customer contact transcript data by digesting the API call through CS team. The digested data would be processed via AWS SageMaker. The corresponding AWS Account would be Anvil Certified for processing critical and highly confidential data. The processed data would be stored in Elastic Data eXchange (EDX)_,_ a centralized and secure metadata store for all Amazon data. EDX provide additional security for AWS S3 data stroage and it supports critical and highly confidential data. See [https://w.amazon.com/bin/view/EDX/FAQ#HSecurity](https://w.amazon.com/bin/view/EDX/FAQ#HSecurity) for additional knowledge on the sercurity of EDX storage.

